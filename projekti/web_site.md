topic: Projekti
title: Web Site

Ovaj tekst je namenjen kao pomoc onima koji zele da naprave sajt slican ovom sajtu. Ako imate pitanja slobodno ih postavite u komentarima na dnu strane.

---

[TOC]

---

#Koriscene tehnologije

[Flask]:http://flask.pocoo.org
[markdown]:http://daringfireball.net/projects/markdown/
[Flask-FlatPages]:http://pythonhosted.org/Flask-FlatPages/

Ovaj web site je napravljen koristeci `Python` kao i pakete `flask`, `FlatPages`, `Frozen-Flask` i `markdown`.

Kao web-framework za razvoj sajta koriscen je **[Flask]**.

> Flask is a microframework for Python based on Werkzeug, Jinja 2 and good intentions. And before you ask: It's BSD licensed!

Ceo sajt se dinamicki generise iz fajlova koji su u **[markdown]** formatu koristeci pakete `markdown` i `FlatPages`. Paket `markdown` generise `html` od `markdown` fajlova kojima se pristupa pomocu paketa `FlatPages`.

> Markdown is a text-to-HTML conversion tool for web writers. Markdown allows you to write using an easy-to-read, easy-to-write plain text format, then convert it to structurally valid XHTML (or HTML).

<!-- -->

> **[Flask-FlatPages]** provides a collections of pages to your **[Flask]** application. Pages are built from “flat” text files as opposed to a relational database.


Vise o koriscenim paketima mozete pronaci na: 

* <http://pythonhosted.org/Markdown/>
* <http://flask.pocoo.org>
* <http://pythonhosted.org/Flask-FlatPages/>
* <http://pythonhosted.org/Frozen-Flask/>

Pakete mozete instalirati koristeci `pip`.

	pip install markdown
	pip install flask
	pip install Frozen-Flask
	pip install Flask-FlatPages

Vise o `pip`-u mozete pronaci na <https://pypi.python.org/pypi/pip>.

Nakon sto nabavite sve potrebne pakete mozete pokusati da napravite svoj sajt pomocu izvornog koda i template-a datih u nastavku teksta.

##virtualenv
	
Preporucujem da se za rad na projektima u `python`-u za svaki projekat koji zavisi od nekih paketa kreira virtuelno okruzenje koristeci `virtualenv`.

> `virtualenv` is a tool to create isolated Python environments.

`virtualenv` mozete instalirati sledecom komandom:

	pip install virtualenv

Virtuelno okruzenje se pravi komandom:

	virtualenv IME_OKRUZENJA
	
Pre koriscenja virtuelnog okruzenja ono se mora aktivirati komandom:

	source IME_OKRUZENJA/bin/activate

Vise o `virtualenv`-u mozete pronaci na: <http://virtualenv.org>

Kada instalirate i aktivirate `virtualenv` sve potrebne pakete mozete instalirati iz fajla `requirements.txt` komandom:

	pip install -r requirements.txt 
	
Sadrzaj fajla `requirements.txt`:

	Flask==0.9
	Flask-FlatPages==0.3
	Frozen-Flask==0.9
	Jinja2==2.6
	Markdown==2.2.1
	PyYAML==3.10
	Pygments==1.6
	Werkzeug==0.8.3
	wsgiref==0.1.2

#Tema

Koriscena tema je modifikovana verzija teme [Midnight by mattgraham](https://github.com/mattgraham/Midnight).

# Source code

	:::python
	# file:   site.py
	# author: ntrifunovic
	
	import os
	import sys
	
	from flask import Flask, request, url_for, render_template
	from flask_flatpages import FlatPages, pygments_style_defs
	from flask_frozen import Freezer
	
	import markdown
	import mdx_mathjax
	
	if not 'HEROKU' in os.environ:
	    DEBUG = True
	
	FLATPAGES_EXTENSION = '.md'
	
	def my_markdown(text):
	    import pygments
	
	    extensions = ['mathjax', 'codehilite', 'toc', 'abbr']
	    return markdown.markdown(text, extensions)
	
	FLATPAGES_HTML_RENDERER = my_markdown
	
	app = Flask(__name__)
	app.config.from_object(__name__)
	pages = FlatPages(app)
	freezer = Freezer(app, with_static_files = False)
	
	
	@app.route('/')
	def index():
	    spages = sorted(pages, 
	                    key = lambda page: (page['topic'] if 'topic' in page.meta else None,
	                                        page['order'] if 'order' in page.meta else None,
	                                        page['title']))
	    return render_template('index.html', pages = spages)
	
	@app.route('/pygments.css')
	def pygments_css():
	    return pygments_style_defs('native'), 200, {'Content-Type': 'text/css'}
	
	@app.route('/<path:path>/')
	def page(path):
	    spages = sorted(pages, 
	                    key = lambda page: (page['topic'] if 'topic' in page.meta else None,
	                                        page['order'] if 'order' in page.meta else None,
	                                        page['title']))
	    return render_template('doc.html', output = pages.get_or_404(path), pages = spages)
	
	if __name__ == "__main__":
	    if len(sys.argv) > 1 and sys.argv[1] == "build":
	        freezer.freeze()
	    else:
	        port = int(os.environ.get('PORT', 5000))
	        app.run(host='0.0.0.0', port=port)
	        
	        
#Templates

`Flask` kao podrazumevani templating sistem koristi `Jinja` template engine. Sve templejte treba staviti u folder `templates` koji treba napraviti u istom folderu u kome se nalazi source code.

>Jinja2 is a full featured template engine for Python. It has full unicode support, an optional integrated sandboxed execution environment, widely used and BSD licensed.

Vise informacija mozete pronaci na: <http://jinja.pocoo.org>

##base.html
	
	{#
	  title:  base.html
	  author: ntrifunovic
	#}
	
	{% macro full_title(page) -%}
	  {% if page.topic %}
	    {{ page.topic }} \
	  {% endif %}
	
	  {#
	
	  {% if page.order %}
	    {{ page.order }} .
	  {% endif %}
	
	  #}
	
	  {{ page.title }}
	  {{ caller() }}
	{%- endmacro %}
	
	{% macro pritty_title(page) -%}
	  <h1>{{ page.title }}</h1>
	  {% if page.topic %}
	     <p>
	       -{{ page.topic }}-
	     </p>
	  {% endif %}
	  {{ caller() }}
	{%- endmacro %}
	
	<!doctype html>
	<html>
	  <head>
	   <meta charset="UTF-8">
	   <meta http-equiv="X-UA-Compatible" content="chrome=1">
	   <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no">
	
	   <title>{% block up_title %}ntrifunovic{% endblock %}</title>
	   <link rel="stylesheet" href="{{ url_for('pygments_css') }}">
	   <link rel="stylesheet" href="{{ url_for('static', filename='stylesheets/styles.css') }}">
	   <script src="//ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>
	   <script>
	     var _gaq = _gaq || [];
	     _gaq.push(['_setAccount', 'UA-38492106-1']);
	     _gaq.push(['_trackPageview']);
	
	     (function() {
	     var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
	     ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js';
	     var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
	     })();
	   </script>
	   {% block extra_scripts %}
	   {% endblock extra_scripts %}
	  </head>
	  <body>
	      <div id="header">
	        <nav>
	          <li class="fork"><a href="{{ url_for('index') }}">Home</a></li>
	        </nav> 
	      </div><!-- end header -->
	  
	
	      <div id="index">
	        {% block nav %}
	        <h3><b>NAVIGACIJA:</b></h3>
	        <ul>
	          {% for page in pages %}
	          <li>
	            <a href="{{ url_for("page", path=page.path) }}" class="index-item">{% call full_title(page) %}{% endcall %}</a>
	          </li>
	          {% else %}
	          <li>No stuff.</li>
	          {% endfor %}
	        </ul>
	        <hr>
	        {% endblock nav %}
	      </div>
	
	
	    <div class="wrapper">
	      <section>
	        <div id="title">
	          {% block title %}{% endblock %}
	          <hr>
	          <span class="credits left">
	            Project maintained by <a href="https://github.com/ntrifunovic">ntrifunovic</a>
	          </span>
	          <span class="credits right">Theme by <a href="http://twitter.com/#!/michigangraham">mattgraham</a> <b>modified</b> by <a href="https://github.com/ntrifunovic">ntrifunovic</a></span>
	        </div>
	
	        <hr>  
	        </section>
	        {% block content %}
	          {{ output|safe }}
	        {% endblock content %}
	
	    </div>
	
	    <div id="footer-bar">
	      <div id="footer-bar-content">
	        <hr class="spaceless">
	
	        <span id = "social">
	          SOCIAL CORNER
	        </span>
	
	        <hr class="spaceless">
	
	        {# FB LIKE #}
	        <span id="fb-like-b">
	          <div class="fb-like" data-send="true" data-layout="button_count" data-width="50" data-show-faces="true"></div>
	              <div id="fb-root"></div>
	              <script>(function(d, s, id) {
	                var js, fjs = d.getElementsByTagName(s)[0];
	                if (d.getElementById(id)) return;
	                js = d.createElement(s); js.id = id;
	                js.src = "//connect.facebook.net/en_US/all.js#xfbml=1";
	                fjs.parentNode.insertBefore(js, fjs);
	                }(document, 'script', 'facebook-jssdk'));
	              </script>
	        </span>
	
	        <hr class="spaceless">
	
	        {# TWEET #}
	        <span id="tweetb-b">
	          <a href="https://twitter.com/share" class="twitter-share-button" data-size="medium">Tweet</a>
	          <script>!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0];if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src="//platform.twitter.com/widgets.js";fjs.parentNode.insertBefore(js,fjs);}}(document,"script","twitter-wjs");</script>
	        </span>
	
	        <hr class="spaceless">
	
	        {# GOOGLE +1 #}
	        <span id="google-pb">
	          <!-- Place this tag where you want the +1 button to render. -->
	          <div class="g-plusone" data-size="medium"></div>
	
	          <!-- Place this tag after the last +1 button tag. -->
	          <script>
	            (function() {
	            var po = document.createElement('script'); po.type = 'text/javascript'; po.async = true;
	            po.src = 'https://apis.google.com/js/plusone.js';
	            var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(po, s);
	            })();
	          </script>
	        </span>
	
	        <hr class="spaceless">
	
	      </div>
	    </div>
	  </body>
	</html>

##index.html

	{#
	  title: index.html
	  author: ntrifunovic
	#}
	
	
	{% extends "base.html" %}
	
	{% block content %}
	<section id="naslovna">
	  <div id="title">
	    <h1>
	      <b> 
		DOBRO DOSLI	:)
	      </b>
	    </h1>
	  </div>
	  <hr class = "spaceless">
	  <a href="http://rs.linkedin.com/in/ntrifunovic/">
	    <img src="{{ url_for('static', filename='images/ja_2.jpg') }}" class = "spaceless">
	  </a>
	  <hr class = "spaceless">
	</section>
	
	{% endblock %}
	
##doc.html

	{#
	  title:  doc.html
	  author: ntrifunovic
	#}
	
	{% extends "base.html" %}
	
	{% block extra_scripts %}
	<script type="text/x-mathjax-config">
	  MathJax.Hub.Config({
	    tex2jax: {
	      inlineMath: [ ['$','$'] ],
	      displayMath: [ ['$$','$$'] ],
	      processEscapes: true
	    },
	  });
	</script>
	<script
	  src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
	</script>
	{% endblock %}
	
	{% block title%}
	{% call pritty_title(output) %}{% endcall %}
	{% endblock %}
	
	{% block up_title %}
	{% call full_title(output) %}{% endcall %}
	{% endblock %}
	
	{% block content %}
	   {{ super() }}
	   <hr>
	   {# DISQUS #}
	    <div id="disqus_thread"></div>
	    <script type="text/javascript">
	        /* * * CONFIGURATION VARIABLES: EDIT BEFORE PASTING INTO YOUR WEBPAGE * * */
	        var disqus_shortname = 'ntrifunovic'; // required: replace example with your forum shortname
		var disqus_title = '{{ output.topic }}\\{{ output.title }}';
		var disqus_identifier = '{{ output.topic }}\\{{ output.title }}';
	
	        /* * * DON'T EDIT BELOW THIS LINE * * */
	        (function() {
	            var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
	            dsq.src = 'http://' + disqus_shortname + '.disqus.com/embed.js';
	            (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
	        })();
	    </script>
	    <noscript>Please enable JavaScript to view the <a href="http://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
	    <a href="http://disqus.com" class="dsq-brlink">comments powered by <span class="logo-disqus">Disqus</span></a>
	    
	{% endblock content %}
	
#Prmer stranice u Markdown formatu

	topic: Uvod u C++
	order: 7
	title: Pokazivaci
	
	**(eng. Pointers)**
	
	* Promenjiva tipa pokazivac na neki tip se deklarise na sledeci nacin
	
			tip *imePokazivaca;
			
	* Vrednost pokazivaca predstavlja adresu u memoriji na kojoj se nalazi promenjiva onog tipa koji je koriscen pri deklaraciji pokazivaca
	* Memoriskoj lokaciji na koju ukazuje pokazivac pristupamo unarnim prefiksnim operatorom `*`
	* Unarni prefiksni operator `&` vraca adresu podatka u memoriji
	* Za pristup elementima strukture preko pokazivaca koristi se operator `->`
	* Pokazivaci se ponasaju kao i drugi podaci
		* Mogu se praviti nizovi pokazivaca
		* Strukture u sebi mogu sadrzati pokazivace
	
	
	**Primer:**
	
		int x = 10;
		int *px = &x, y; // y nije pokazivac
		*px = 3;
		y = x;
	
	*Koja je vrednost u promenjivoj y ?*
	> Resenje: 3
	
		// Pristupanje elementima strukture preko pointera
		Tacka *pt = &t;
		(*pt).x = 0;
		pt->y = 0;

#Free Hosting

Ovaj website koristi free hosting i dostupan ja na dve adrese <http://ntrifunovic.github.com> i <http://ntrifunovic.herokuapp.com>.

Vise o free hosting-u koji ovaj website koristi mozete pronaci na:

* <http://pages.github.com> ( **github pages** moze da host-uje samo staticki sadrzaj. Za generisanje statickog website-a koriscen je paket `Frozen-Flask`)
* <http://www.heroku.com> ( **Heroku** daje samo 1 *web dyno* free po website-u )
