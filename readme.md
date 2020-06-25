Vue - for beginners
======================

[# 1 - Vue.js for beginners - connection and first steps | vue lessons | vue.js 2.x | 2.5.x (6:51)]( https://www.youtube.com/watch?v=9dJQ8yXqizI&list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&index=1 )

_You will learn how to connect and use `vue` in your projects, it will be interesting!_

* ***Actions:***

Сommands:

	//cd /var/www/LARAVEL/VUE/vue_begin
	sudo chmod -R 777 /var/www/LARAVEL/VUE/vue_begin
	
	// !!! .conf 
	sudo cp /etc/apache2/sites-available/test.loc.conf /etc/apache2/sites-available/vue_begin.conf 	
	sudo nano /etc/apache2/sites-available/vue_begin.conf
	
	sudo a2ensite vue_begin	
	sudo service apache2 restart
	sudo nano /etc/hosts

Сode:

```html	
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css" integrity="sha384-9aIt2nRpC12Uk9gS9baDl411NQApFmC26EwAOH8WgZl5MYYxFfc+NcPb1dKGj7Sk" crossorigin="anonymous">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css">

<script src="https://code.jquery.com/jquery-3.5.1.min.js" integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+OGpamoFVy38MVBnE+IbbVYUew+OrCXaRkfj" crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js" integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldlvI9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/js/bootstrap.min.js" integrity="sha384-OgVRvuATP1z7JjHLkuOU7Xw704+h835Lr+6QL9UvYjZE3Ipu6Tp75j7Bh/kR0JKI" crossorigin="anonymous"></script>

<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>

<div id="dka">
  {{ message }}
</div>

<script type="text/javascript">
    var app = new Vue({
        el: '#dka',
        data: {
            message: 'Hello Vue!'
        }
    })
</script>
```

Welcome to the first series of lessons devoted to the introduction and understanding of the basics of working with such an excellent framework as `Vue`. (- Pronounced like` View`).
Opportunities and ease of operation - this is its main difference from the more complex `REACT | ANGULAR` etc. `Vue.js` does NOT use the `virtual DOM`, but works directly with it,
as a template, keeping links to existing nodes for linking. This DOM is reactively linked. The main rule is to call the Vue instance
IF `DOM` is already loaded - OTHERWISE it will NOT work.

[(1:00)]( https://youtu.be/9dJQ8yXqizI?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=60 ) 

![screenshot of sample]( https://github.com/mslobodyanyuk/dka-develop_vue_begin/blob/master/public/images/1(1).png )

So, let's show that at the end of the tutorial series of lessons we will do:
- Heading with a variable And increasing the value of a variable by 1-tsu.
- Tracking the state of the radio buttons, affecting the color of the border of the form block, in this case, the class will change. Blocks and markup elements will be hidden,
reset values ​​of variables.
- Asynchronous requests from remote sites will be used.
In this example, we will request a List of channels and hashtags from our site, https://dka-telegram.ru - a directory of telegram channels - Bidirectional data binding.
- Work with Lists and Observers.
- Handling Events from the Keyboard. etc.
We will consider the most necessary and what will give you an idea and initial experience for further work.

[(2:00)]( https://youtu.be/9dJQ8yXqizI?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=120 ) We will use the empty `HTML5` template and a regular file with the extension `.html`. You do NOT need any web server (`Apache | Nginx`). To ALL was more concise we will use
`Bootstrap`, we will use version 4. It is worth mentioning that Vue does NOT need anything to work, it is almost self-sufficient (NO `jQuery`, NO `Bootstrap`). You can connect ONLY `Vue` and EVERYTHING.
BUT ALL some of the possibilities in it are NOT inherent. The main thing that delivery does not include is Routing OR ajax functions (`jQuery.ajax () | jQuery.get ()`), out of the box, and as a rule
assumes that you are building the application using an external module. - Therefore, we will use `jQuery`, as it is familiar to many. - For someone who does NOT need `jQuery` - maybe
use `axios` (- https://github.com/axios/axios).

[(2:45)]( https://youtu.be/9dJQ8yXqizI?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=165 ) So, let's connect Bootstrap ( - http://getbootstrap.com/ ) The style is connected at the top:

```html		
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css" integrity="sha384-9aIt2nRpC12Uk9gS9baDl411NQApFmC26EwAOH8WgZl5MYYxFfc+NcPb1dKGj7Sk" crossorigin="anonymous">
```
	
`script` - down below:

```html	
<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js" integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+OGpamoFVy38MVBnE+IbbVYUew+OrCXaRkfj" crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js" integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldlvI9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/js/bootstrap.min.js" integrity="sha384-OgVRvuATP1z7JjHLkuOU7Xw704+h835Lr+6QL9UvYjZE3Ipu6Tp75j7Bh/kR0JKI" crossorigin="anonymous"></script>
```	

We will use full-fledged `jQuery` as in` slim 'there is NO `ajax`.

[(3:15)]( https://youtu.be/9dJQ8yXqizI?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=195 ) Let's enable font-awesome to use the icons. We remind you that this is ONLY for decoration.

[(3:20)]( https://youtu.be/9dJQ8yXqizI?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=200 ) Now go to the Vue website (- https://vuejs.org/) -> Get Started. As said here, create index.html and plug in Vue. - You need to connect it at the very bottom.

```html	
<!-- development version, includes helpful console warnings -->
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```	

Please note that we DO NOT download scripts to the local computer, but use cdn, so Vue will work IF your computer has Internet access. IF THE INTERNET
weak - download and write down the local path to the scripts.

[(4:00)]( https://youtu.be/9dJQ8yXqizI?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=240 ) Now, according to the proposed option, we derive something like `` Hello World! '' To check EVERYTHING WE have done correctly. Add a block element with `id = app` (- change the name to your own).
By the way, it can be any:

```html	
<div id="dka">
```	
And add the javascript block at the very bottom, below the connected scripts:

```html	
	<script type="text/javascript">...
```
	
Rename the item id to `#dka`:

```html	
<script type="text/javascript">
	var app = new Vue({
	  el: '#dka',
	  data: {
		message: 'Hello Vue!',
		getDate: 'Текущее время: ' + new Date().toLocaleString()
	  }
	})
</script>
```
		
`new Vue` is the basic initialization, then it is necessary to pass the recommended parameters:
1st element, it is needed for `bind` OR the word used in Russian is `template bind`. The main element in which `Vue` will be used.
The next element, `data`, is responsible for storing and initializing our variables that will be used. ALL variables must be declared here. The output of variable values ​​like `echo` in `PHP` is done
using `{{}}`. Note that in LARAVEL and the Blade template engine the same notation is used. IF you want to use `Vue` in the file `Blade` - you must use the symbol `"@"` - then the template engine
will ignore this entry. In general, I recommend using `Vue-components` in `LARAVEL` which we will definitely consider using the example of a `LARAVEL-project`.

[(5:30)]( https://youtu.be/9dJQ8yXqizI?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=330 ) We look in the browser, `tutorial.html`, what we got.
"Hello Vue!" - Great, EVERYTHING works.
  Now let's see how to use variables in attributes.

[(5:50)]( https://youtu.be/9dJQ8yXqizI?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=350 ) To do this, use the `v-bind:` attribute name (`v-bind: title =" getDate "`), or you can simply `: title`, then the variable name (`: title = "getDate" `) .
	
```html	
<label for="" title="getDate">Проверка времени</label> 
```	
	
[(6:00)]( https://youtu.be/9dJQ8yXqizI?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=360 )Add a new variable (`getDate`) - the time with the signature will be generated:
`getDate: 'Current time:' + new Date (). toLocaleString ()`
Check-update in the browser. - Great, EVERYTHING works. IF NOT to specify `:` OR `v-bind` - then nothing will work. In the following lessons, consider the most useful hooks:
`created`, `watch`, `methods`, etc.

---


[#2 - Vue.js v-model и methods | vue уроки | vue.js 2.x | 2.5.x		(4:59)]( https://www.youtube.com/watch?v=mYcOBwn7Ji4&list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&index=2 )

_You will learn: tracking the state of radio buttons, changing classes using `vue.js` and bidirectional data binding._

* ***Actions:***

<https://github.com/dka-develop/vuejs-new-tutorial> - copied the code to `/var/www/LARAVEL/VUE/vue_begin/tutorial_2.html`

Today we will learn the `methods` hook And the Header with the variable And incrementing the variable by 1-tsu.

- Tracking the state of the radio buttons affecting the color of the border of the form block. In this case, the class will change.
- Bidirectional data binding V-MODEL. Take the file from the 1st lesson and make a duplicate. (- You can take it from the repository on github - 
<https://github.com/dka-develop/vuejs-new-tutorial/blob/master/tutorial.html> ).

[(1:00)]( https://youtu.be/mYcOBwn7Ji4?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=60 ) In the previous lesson, we focused on declaring variables in attributes and on the page. In this, let's start with the `methods` hook, add this parameter to the `Vue` construction, curly braces with an array of our methods,
which in essence are functions that we will call.

```html
methods: {
	tutorialDemo: function() {
		this.counter++
	}
}	
```

Declare a variable in the `data` parameter:

```html	
counter: 0 
```	

We’ll increase the value by 1 each time the method is called (Be sure to indicate `"this"` in front of it), that is, the variable OR to any method inside the `Vue` instance:


```html
this.counter++
```	

Otherwise, it will look for the variable in the `var-section`.

[(1:55)]( https://youtu.be/mYcOBwn7Ji4?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=115 ) Create a Header tag, add the Header attribute `@ click` + `the name of our method`, we don’t pass anything to the function, so we won’t even indicate the brackets:


```html
<h1 @click="tutorialDemo">DKA-DEVELOP Tutorial #{{counter}}</h1>
```

[(2:15)]( https://youtu.be/mYcOBwn7Ji4?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=135 ) The output of the value `var counter = 2`, (- See, it started with 2, as indicated in the code). - We remove, check. - Great, it works.

[(2:36)]( https://youtu.be/mYcOBwn7Ji4?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=156 ) Let's create a link and call a method from it.

```html
<a href="#" @click="tutorialDemo">Нажми меня</a>
```	

Updating - great.

[(2:55)]( https://youtu.be/mYcOBwn7Ji4?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=175 ) Let's create some radio buttons with the 1st name, BUT for starters - the form:

```html
<form class="border m-2 p-4" :class="typeJob == 'list' ? 'border-primary' : 'border-danger'">
	<div class="form-row">
	  <div class="form-group col-md-6">
		<div class="form-group">
		  <input type="radio" name="type" v-model="typeJob" value="list" :checked="typeJob == 'list'"> Список каналов
		  <input type="radio" name="type" v-model="typeJob" value="search" :checked="typeJob == 'search'"> Поиск
		</div>
	  </div>
	</div>
</form>
```

[(3:30)]( https://youtu.be/mYcOBwn7Ji4?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=210 ) What do we have here? - We use `V-MODEL` for two-way communication of our variable. The second feature is the `: checked` attribute which will have
boolean value. That is, `true` IF the variable is `typeJob == 'list'` OR `'search'`. Declare the variable `typeJob` in the parameter `'data'`, by default it will have
value. Let's add another class change depending on the value of our `typeJob` variable:

```html
<input type="radio" name="type" v-model="typeJob" value="list" :checked="typeJob == 'list'"> Список каналов
<input type="radio" name="type" v-model="typeJob" value="search" :checked="typeJob == 'search'"> Поиск
```	

IF `true` - such-and-such, ELSE - the border will be red.

[(4:20)]( https://youtu.be/mYcOBwn7Ji4?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=260 ) We display the value of the variable on the page for visual definition.

[(4:40)]( https://youtu.be/mYcOBwn7Ji4?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=280 ) We are updating the page. - As you can see, the class has changed and two-way communication is working.

---


[#3 - Vue.js watch | v-for | ajax | vue lessons | vue.js 2.x | 2.5.x		(11:48)]( https://www.youtube.com/watch?v=7t_SU3oFljA&list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&index=3 )

_You will learn how to connect and use vue in your projects, it will be interesting!_

* ***Actions:***

<https://github.com/dka-develop/vuejs-new-tutorial> - copied the code to `/var/www/LARAVEL/VUE/vue_begin/tutorial_3.html`

Today we will learn the hooks `watch`, `created`, `AJAX (jQuery)`. Work with V-FOR Lists and Observers. - Take the file from the 2nd lesson and make a duplicate.
( - You can download from the repository on github -

<https://github.com/dka-develop/vuejs-new-tutorial/blob/master/tutorial_3.html> 

). 

In the previous lesson, we settled on the radio buttons and the method call in `Vue`. - In this, we start with the `watch` hook, add this parameter to the `Vue` construction:

```html
watch: {
search: function() {
  this.search.length >= 2 ? this.lookupHashtag() : this.hashtags = [];
},
typeJob: function() {
  this.typeJob == 'list' ? this.lookupChannel() : this.hashtags = [];
  this.checkPick = []
}
},
```

What does `watch` do? - In fact, this is an observer, he looks at changes in data in variables and objects. Before adding an object, let's create
html input element:

```html
<div v-if="typeJob == 'search'" class="form-group">
	<input type="text" class="form-control" name="search" v-model="search" placeholder="Введите искомое значение"></input>	
</div>
```
	
This element will be visible IF the value of the `typeJob` radio element is equal to `'search'`. Our `input`, name is `search`, bidirectional data binding
`v-model`. - Add this variable to our `Vue`.

[(2:00)]( https://youtu.be/7t_SU3oFljA?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=120 ) Let's keep track of the input and the number of characters in another html element. Also displays IF `search` search, display the value of the variable
to the page:

```html
<div v-if="typeJob == 'search'" class="form-group">
	<label>Поиск: {{search}}</label> 
	<label v-if="search.length">- кол-во символов {{search.length}}</label>
</div>
```

[(2:42)]( https://youtu.be/7t_SU3oFljA?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=162 ) - Check, refresh the page. - Well.

[(3:00)]( https://youtu.be/7t_SU3oFljA?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=180 ) Returning to the observer, we will monitor the state of the `search` variable. IF the number of characters is `> = 2`, then execute the method called `lookupHashtag`.
ELSE, we will clear the variable with the contents of the remote response from the SERVER.

[(3:30)]( https://youtu.be/7t_SU3oFljA?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=210 ) We need to create this lookupHashtag method. - We do it by analogy, add `ajax` from `jQuery`, `url` is the path, the path where we are accessing. To check
we will use our site of telegram channels which returns data in the `json` format:

```html	
	lookupHashtag: function() {
	  $.ajax({
		url: app.url.hashtags,
		dataType: 'json',
		data: {name : app.search},
		success: function( json ) {
		  app.hashtags = json
		}
	  });
	},
```	
	
[(3:55)]( https://youtu.be/7t_SU3oFljA?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=235 ) By the way, pay attention, IF someone is NOT familiar with the concept of `Cross-Domain Requests` - this is for example when using the `ajax` method OR any other request using
`javascript` access from this computer OR your domain, for example mydomain.ru to another domain -> dka-develop.ru. - This is called the Cross Domain Request.
And the SERVER receiving the request must explicitly allow this kind of Request.

[(4:20)]( https://youtu.be/7t_SU3oFljA?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=260 ) To do this, he must give the header - `header("Access-Control-Allow-Origin:*")`
An example for PHP, where `*`  means - EVERYTHING. Instead, we can also specify a specific domain. IF you access inside your domain, site, etc. you don’t
you need to bother - it will work so. `dataType` - type of data received, `data` - the value of our variable, the first parameter in brackets is the key OR
name in the Request, 2nd - the value of the `search` variable from our `Vue instance`. The value of the variable `'hashtags'` will be equal to the response of the SERVER. Note
how the call is written inside the `ajax variable`. It is important. IF we write `this`, then the search for our variable will be inside our `ajax` function. We
specify the name of the `Vue instance` ( `app` or any, for example `dka` ). IF you DO NOT assign the name of the `Vue instance`, there is a way out: before `ajax` we write `var dka = this`. - It will work the same as
and in the previous entry.

[(5:40)]( https://youtu.be/7t_SU3oFljA?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=340 ) Let's add our variable to `Vue`.

[(5:50)]( https://youtu.be/7t_SU3oFljA?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=350 ) Getting started with Lists. That is, we will process the array of received data from the SERVER in a loop.
Example server response (json):

array = ['#it', '#itanalytics', '#ithack', '#itoffice', '#ittechnology']

[(6:15)]( https://youtu.be/7t_SU3oFljA?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=375 ) Display IF Search `search` And the `v-for` directive - there are 2 entries - `(key, value) in` And our variable with the SERVER answer that we iterate over:

```html	
<div v-if="typeJob == 'search'" class="form-check" v-for="(value,index) in hashtags">
```
	
The second entry WITHOUT brackets, only an array element:

```html
<div v-if="typeJob == 'search'" class="form-check" v-for="hashtag in hashtags">
```

We will output in the form of a checkbox. Bidirectional data binding with a new variable necessary for tracking selected list items AND assigning checkbox:

```html
<input type="checkbox" class="form-check-input" v-model="checkPick" :value="hashtag">
```	

Display the name of the checkbox:

```html
{{hashtag}}
```	

Let's display the selected checkbox on the page. First, add a Vue instance:

```html
checkPick: [],
```	
	
- Display IF the number of selected items is greater than 0. - The output will be simple:

```html
<div v-if="checkPick.length" class="form-group">
  {{checkPick}} - {{checkPick.length}}
</div>
```
	
[(7:28)]( https://youtu.be/7t_SU3oFljA?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=448 ) We proceed to the demonstration. - Open in the browser (F12) - `Console`, `Network-bookmark`. We mark the radio button, Search - we write `'it'` and we see our Request and Response.

[(7:43)]( https://youtu.be/7t_SU3oFljA?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=463 ) Our list is also drawn on the page. - Click on the `checkbox`. - How simple and functional is the use of `Vue` in your projects.

[(7:55)]( https://youtu.be/7t_SU3oFljA?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=475 ) Let's create a similar method, BUT now we will get just a List. For the practice of accessing variables, create an array with the addresses:

```html
url: {
  hashtags: 'https://dka-telegram.ru/channel/api?type=hashtags',
  channels: 'https://dka-telegram.ru/channel/api?type=channels'
},
```	

And in the method we write:

```html
	url: app.url.hashtags,
```
	
We create the third method. And here, to demonstrate the use of variables, we will indicate as the second method (`var dka = this`), add a new url ( `channels: 'https: //dka-telegram.ru/channel/api? Type = channels'` )
Remove `data` from `lookupChannel`. - We will NOT transfer anything additional. If successful, assign the SERVER response (`dka.channels = json`) to the `channels` variable:

```html	
	lookupChannel: function() {
		  var dka = this
		  $.ajax({
			url: dka.url.channels,
			dataType: 'json',
			success: function( json ) {
			  dka.channels = json
			}
		  });		  
```
		  
Add a new variable to `data` - `channels`:
	
```html	
	channels: [],
```	
	
[(9:18)]( https://youtu.be/7t_SU3oFljA?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=558 ) Let's add a new list. IF the radio button is equal to `'list'`, here for demonstration the record will be with the key. We will change the name by adding a key to the name. - The connection will be the same as And in
previous List And the value will be the `name` field:

```html	
<div v-if="typeJob == 'list'" class="form-check" v-for="(channel, index) in channels">
	<label class="form-check-label">
		<input type="checkbox" name="'channel-' + index" class="form-check-input" v-model="checkPick" :value="channel.name">
		{{channel.name}}
	</label>
</div>
```	
	
[(10:05)]( https://youtu.be/7t_SU3oFljA?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=605 )	You can see that this list, unlike the previous ones, is a multidimensional array:

![screenshot of sample]( https://github.com/mslobodyanyuk/dka-develop_vue_begin/blob/master/public/images/3(10.5).png )

And print the signature:

```html
{{channel.name}}
```	
	
[(10:25)]( https://youtu.be/7t_SU3oFljA?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=625 ) - What remains for us is to add the `observer`. Add it for our radio buttons. IF the value of the variable will be equal to `'list'` - call the method with channels (`lookupChannel`). ELSE -
clear the variable with a list of hashtags. Also, with each change in the value of the radio button, we will reset the variable with the selected elements:

```html
typeJob: function() {
	  this.typeJob == 'list' ? this.lookupChannel() : this.hashtags = [];
	  this.checkPick = []
}
```
	
[(11:11)]( https://youtu.be/7t_SU3oFljA?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=671 ) The last thing we will do is add the `created` hook. - It runs after creating the Vue instance, assigning the value of the `search` radio button:

```html
	created() {
		this.typeJob = 'search'
	},
```
	
- We are updating, EVERYTHING works fine for us.

#### useful links:

[#3 (7:36) [ Error: - Reason: CORS request did not succeed ] ]( https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS/Errors/CORSDidNotSucceed )

[(7:36)]( https://youtu.be/7t_SU3oFljA?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea&t=456 )

[Fetch: requests to other sites](https://learn.javascript.ru/fetch-crossorigin)

				
Useful links:
=============

[Vue - for beginners]( https://www.youtube.com/playlist?list=PLD5U-C5KK50UFbtFxPKlayhdZlOEpWuea )

[GitHub]( https://github.com/dka-develop/vuejs-... )

[Bootstrap]( http://getbootstrap.com/ )

[Vue]( https://vuejs.org/ )

[Axios]( https://github.com/axios/axios )
