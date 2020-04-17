## Week 8 Homework Due Wednesday, April 22 2020 at 6pm

**OMDB Movie Api Project 6:** counts toward **65%** of the **final grade**

**Week 8 Homework Part 2:** counts toward **20%** of the **final grade**

I have **_created_** the **following files** for you:

- `main.js` **file** in `scripts/js/main.js`

- `main.css` **file** in `styles/css/main.css`

- an `index.html` **file** in the `root` of this `week 8 homework folder`.

- **_this_** `README.md` with `instructions`.

- `.gitignore` **file** to `ignore` the **_potential_** `.vscode` which sometimes **_appears_** if you are are **_using_** `VS Code`.

- **_Again_**, `git clone` this `repository` to your **computer**. Then `rm -rf .git` and **_re-initialize_** it. The `index.html` of this `project` **_has to be_** in the `root` of the `folder` and **_not_** within **another folder** when **_pushed_** to `Github`. **_Otherwise_**, when I **test** it **_out_**, it will **not work**. We are dealing with **_retrieving_** `Api data` here, so the `index.html` **_cannot_** be **nested** **_inside_** a **folder**. As you **_should_** already **know**, there can only be **ONE** `index.html` **_per project_** at the `root` of **_it_**.

- **For those of you on Windows:** If you don't know your way around Windows Powershell, don't git clone this repository. Create a new stand alone repository yourself, and copy and paste the folders inside this repository into yours. That way, you won't be inheriting the .git folder that you possibly can't remove, and can git init from a clean slate. If you have any questions, please contact me on Discord. If you want to try removing a .git folder from a dummy repo, you can always use the following one I have created on Github: [test-repo on Github](https://github.com/interglobalmedia/test-repo) Some helpful articles on how to remove files and folders (and other helpful Powershell commands) on Windows in Powershell:

[How to show hidden files and folders on Windows 10](https://pureinfotech.com/show-hidden-files-folders-windows-10/)

[PowerShell equivalents for common Linux/bash commands](https://mathieubuisson.github.io/powershell-linux-bash/)

[Powershell Tutorial](https://www.tutorialspoint.com/powershell/index.htm)

- You will **have to get** an `Api key` in **_order_** to be **able** to **_use_** this `Api`. I normally would **_not_** **ask** anyone to **_get_** an `Api key` for a `client-side only` **_application_**, as the `Api key` would be **exposed** on the `client-side` (**_specifically_** within the **source code** and **_sometimes_** the `index.html`), but this is a **_free_** **Api** which will **_not_** **ask** for your `credit card`, and **_therefore_** **not** be able to charge you. You will obtain it during (remote) class time, so I will be there to guide all of you in how to obtain the Api key and in case if there are any issues or problems.

### OMDB Movie Api Project 6:

This time, I am **_not_** going to **add** **_anything_** other than the **following** in the `index.html`:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>OMDB Api App</title>
  </head>

  <body></body>
</html>
```

- This means that you have to **_add_** the `main.js` file **yourselves** to the `index.html`.

- This means that you have to **_add_** the `main.css` file **yourselves** to the `index.html`.

- PLEASE REMEMBER that IF you are **_adding_** `Google Fonts`, they **_should be_** **placed** ABOVE the `external stylesheet` **link**, NOT BELOW. If you **_place_** the `Google Fonts` **below**, I will **_take off_** **points**.

- As for the **_rest_**, that **depends on** which **elements** you decide to **_use_** in your `main.js` **file**. Make **_sure_** that what you **use there** is **reflected** **_EXACTLY_** in your `index.html`. If there is a **mismatch**, I will **_take off points_** that you **can't** **get back**. **_Check your work carefully_** before **submitting it** to me.

### Building the OMDB Movie Api App:

- **_First_**, go into your `scripts/js/main.js` file. There, `declare` a `function` called `getData()`. So it should look something like **_this_**:

```js
// main.js
function getData() {}
```

- Inside the body of `function getData() {}`, `declare` and `initialize` a **variable** called `movie`. **_Assign_** **it** the **value** of `document.getElementById("movie").value;`.

- Next, under the `movie` **variable**, `declare` and `initialize` a **variable** called `container`. **_Assign_** **it** the **value** of `document.getElementById("container");`.

- Next, under the `container` **variable**, `declare` and `initialize` a **variable** called `url`. **_Assign_** **it** the **value** of the **_following_**:

```js
const url = `https://www.omdbapi.com/?apikey=YOURAPIKEY&t=${movie}`;
```

`${movie}` is the `interpolation` (**insertion**) of the `movie` **variable** that you **_create_** **earlier**.

- Next, you `declare` and `initialize` a **variable** called `xhttps`. **_Remember_** **this variable**, from the [Dynamic Web 1: Using AJAX With Apis](https://interglobalmedia.github.io/dynamic-web-1-omdb-api-ajax/#/) **slide deck**? **_Assign_** **it** the **value** of `new XMLHttpRequest()`.
- Now we get to the fun part! **_Next_**, set the `onreadystatechange` property on the `xhttps` **variable**. **_Initially_**, **assign it** the **value** of `function() {}`.

```js
xhttps.onreadystatechange = function () {};
```

- Next, **_inside_** the **body** of the `anonymous function` represented by `{}` (**_above_**), add an `if statement`. **Inside** the `()` **_after_** the `if` **keyword**, **_add_** `this.readyState === 4 && this.status === 200`. At **_this point_**, your `if statement` should look like **_this_**:

```js
if (this.readyState === 4 && this.status === 200) {
}
```

`this` **points to** the `xhttps` **XMLHttpRequest Object** we have **_created_** with the **value** of `new XMLHttpRequest()` This creates a (new) `instance` of the `XMLHttpRequest Object`. In other words, `this` represents the `XMLHttpRequest Object`. Whenever you see `this` being used, **_know_** that it is **always referring** to the **_same_** `XMLHttpRequest Object`. In addition, the **_reason_** we **use** an `anonymous function`, `function() {}`, for the `callback function` **inside** the `xhttps.onreadystatechange` **expression**, is because **functions** using the `function` **keyword** return `this`, which means that `this` points to the `object` in which the `function callback` is **stored** as its **_value_**. if we had used an `arrow function` **_instead_**, it would **_not have_** **pointed** to the `XMLHttpRequest Object`, but to the `global Window Object`. In other words, `globalThis`.

- **_Inside_** the `if statement` **block** **_represented by_** `{}`, at the top of it, **_add_** the **following** `console.log()`:

```js
console.log(this.responseText);
```

**_Remember this_** from the [Dynamic Web 1: Using AJAX With Apis](https://interglobalmedia.github.io/dynamic-web-1-omdb-api-ajax/#/) **slide deck**? This `console.log()` **tests** whether your `XMLHttpRequest()` was successful. If you **_go into_** the `Chrome Developer Tools`, if your `request` was **_successful_**, you will **see** an `Object` with a `dropdown arrow`. `Click` on the `arrow`, and a whole bunch of `Api` **related information** as well as `JavaScript Object` **related information** will appear there. Just as I **_demonstrate_** during the **lecture**. Visit the `recorded video` (which I will **_add_** the **link for** **_after_** the **lecture** is **_over_**) to **refresh** your **knowledge**.

- **_Next_**, you are going to create another `console.log()` and **pass it** a **value** of `JSON.parse(this.responseText)`. The `JSON.parse()` method **does** the **_following_**:

  - `JSON.parse()` **parses** your `Api data`, and the `JSON data` **_becomes_** a `JavaScript object`. That is why `Object` (with the `dropdown arrow` in the `Chrome Developer Tools console`) is **_able_** to be **rendered** and **displayed** to the `console` in the **form** of a `JavaScript Object` **containing** **_all_** the **information** it **_contains_**. Like this:

```js
console.log(JSON.parse(this.responseText));
```

But we **_can't_** **use** the `data` in **_this format_**, **passing it** in the **form** of a `built-in method` **_inside_** of a `console.log()`. We **_have to_** **store it** as the `value` of a **variable**.

- So **_next_**, **below** the `console.log()` you have **_created_** **right above**, `declare` and `initialize` a **variable** called `data`. **_Assign_** **it** the **value** of `JSON.parse(this.responseText);`. This is **_analogous_** to `ip = geoIp` in our `Geo Ip App` we **_created_** for `Project 4`.

- **_Next_**, we have to **_set_** the `innerHTML` **property** on the `various elements` we **_add_** to our `index.html` in order to **render** our `OMDB Api data` to the **_page_**.

- We have to **decide** **_what_** `data` we want to **retrieve** from the `Api`. The following is the `JSON` that I **_first receive_** from the `OMDB Api` in the form of `console.log(this.responseText);`:

```json
{
  "Title": "Blade Runner",
  "Year": "1982",
  "Rated": "R",
  "Released": "25 Jun 1982",
  "Runtime": "117 min",
  "Genre": "Action, Sci-Fi, Thriller",
  "Director": "Ridley Scott",
  "Writer": "Hampton Fancher (screenplay), David Webb Peoples (screenplay), Philip K. Dick (novel)",
  "Actors": "Harrison Ford, Rutger Hauer, Sean Young, Edward James Olmos",
  "Plot": "A blade runner must pursue and terminate four replicants who stole a ship in space, and have returned to Earth to find their creator.",
  "Language": "English, German, Cantonese, Japanese, Hungarian, Arabic",
  "Country": "USA, Hong Kong, UK",
  "Awards": "Nominated for 2 Oscars. Another 12 wins & 16 nominations.",
  "Poster": "https://m.media-amazon.com/images/M/MV5BNzQzMzJhZTEtOWM4NS00MTdhLTg0YjgtMjM4MDRkZjUwZDBlXkEyXkFqcGdeQXVyNjU0OTQ0OTY@._V1_SX300.jpg",
  "Ratings": [
    { "Source": "Internet Movie Database", "Value": "8.1/10" },
    { "Source": "Rotten Tomatoes", "Value": "90%" },
    { "Source": "Metacritic", "Value": "84/100" }
  ],
  "Metascore": "84",
  "imdbRating": "8.1",
  "imdbVotes": "658,507",
  "imdbID": "tt0083658",
  "Type": "movie",
  "DVD": "27 Aug 1997",
  "BoxOffice": "N/A",
  "Production": "Warner Bros. Pictures",
  "Website": "N/A",
  "Response": "True"
}
```

All the `properties` **_above_** (to the **left**) are what we **use** to **_retrieve_** the `Api data`. All the `property` **_values_** (to the **right**) are the actual `data` that is **rendered** to the `page/web browser window`. **Example**:

```js
document.getElementById("director").innerHTML = data.Director;
```

We **start** with the `Director` **property** and not the **movie** `title` **property**, because we already are retrieving the `movie object/variable` by **storing** the `url`

```
`https://www.omdbapi.com/?apikey=YOURAPIKEY&t=${movie}`;
```

as the **value** of the `movie` **constant variable** we `declare` and `initialize` at the **top** of the **_body_** of the `getData() function`. The **movie** `title` **property** is set with

```js
&t=${movie}
```

and by **setting** the `value` **property** on `document.getElementById("movie")`, which is **_passed_** as the **value** of the `movie` **variable**:

```js
const movie = document.getElementById("movie").value;
```

As **_indicated_** in the `OMDB Api documentation`, `t` refers to the `Movie title to search for` parameter. The `?` **_refers to_** the `query` **itself**. Anything after `?` are the **parameters** used to **make** the **query**. In our case **_here_**, the **first parameter** is our `api key`, whose `value` **equals** (=) our **actual** `api key`, **_followed by_** the `&`, which stands for `and`, **_meaning_** we are **adding** a **_second parameter_**, the `t`, whose `value` **equals** (=) the `value` **typed inside** the `input element's field` with the `id` of `"movie"`. This `input element` is **_stored inside_** the `movie` **variable**, and is **_retrieved_** by `querying` the **element** by its `id` (as shown right above). The `value` of the `input field` is **_retrieved_** by setting the `value` **property** on `document.getElementById("movie")`. As above.

- The **_next thing_** to **make sure**, is that you have **_actually_** **added** an `input element` **tag** to your `index.html` that **_contains_** the `id` of `"movie"`. Since it is **_meant_** to **be** an `input` whose `value` is being **_extracted_** by **appending** the `.value` property to `document.getElementById("movie").value`, then **make sure** to **_add_** an `input tag/element` to `index.html` that **contains** the `id` `"movie"`.

The **same process** goes for the **_rest_** of the `OMDB Api` **properties** **_related to_** the `movie title query` and their **_respective_** **values** you want to **fetch** from the `Api`. For example, I **_also fetch_** the `director` of the `movie` I am **querying**. In my `movies.js` file, I do something like the **_following_**:

```js
document.getElementById("director").innerHTML = data.Director;
```

I have **already** **_made reference_** to this **earlier**, but want to **_hit home_** about the `main.js` vs `index.html` **element matching**. We are **_no longer_** **querying** an `input element`. We are simply `querying` an `element` in which we can **render** some **text**. We use the `innerHTML` **property** to achieve that, and we set the **_value_** of the `text` to be `data.Director`. `data` is the `object/variable` that **_contains_** the `Api data` **related** to the `movie title` **query**, and we are **_setting_** the `Director` **property** on it. So the `text` **value** will be the `director` of the `movie` we are **querying** in the `input element`. I, for example, use the `span` **tag** to **_render_** the `text value` of **all** the `movie title properties` I am using. However, I also am **_mindful_** to **add** `html markup` to my `index.html` so that my **page** is **_nicely_** **laid out**. **_That part_** is up to you! This is where your **web design skills** should step in. If you have **_any questions_** about how to **approach** **_this_**, please let me know.

- After you have **_queried_** all the `movie title parameters` you want, or **_whatever_** `query parameters` you **choose**, and **set** the `innerHTML` **property** on the `elements` that will **render** the `property values`, it is **time** to **_call_** the `open()` method. We **_do that_** by **setting** it on `xhttps`.

```js
xhttps.open();
```

We **pass** **_three_** `parameter values` (aka arguments) to the `.open()` **method**:

```js
xhttps.open("GET", url, true);
```

This `call` to `open()` **_follows_** the `closing curly brace` of the `xhttps.onreadystatechange` **function** `callback`. Something like **_this_**:

```js
function getData() {
  // place movie, container, url, and xhttps variables here
  xhttps.onreadystatechange = function () {
    if (this.readyState === 4 && this.status === 200) {
      console.log(this.responseText);
      console.log(JSON.parse(this.responseText));
      const data = JSON.parse(this.responseText);
      /* place queries to the elements with ids storing the xhttps object's property values
  here. i.e.,
  document.getElementById("director").innerHTML = data.Director;
*/
    }
  };
  xhttps.open("GET", url, true);
}
```

**Just to recap:**

"GET" is the `method` (the `value` of the `first parameter` **_passed_** to `open()`) we are **using**. We are **requesting** to `"GET"` **data** from the `OMDB Api`.

`url` is the **url** we are **_sending_** our `request` to (the `value` of the `second parameter` **_passed_** in to `open()`).

`true` means that we are **making** the `request` **asynchronously** (the `value` of the `third parameter` **_passed_** to `open()`).

- Finally, we **set** the `send()` **method** on our `xhttps` **object/variable**. This **_call_** to `send()` **immediately follows** the **call** to `open()`, and is **placed** **_right below_** `xhttps.send()`. **Nothing** is **_passed_** in to it. We **_could_** **pass in** a `document`, for example, but we are **_simply_** `"getting"` **data** here, **_not_** `sending data`. We are **_only_** `sending` our `request`.

- The **_last_** **thing** we **_need to do_** in the `main.js` file of our application is `query` for our `submit button` by `id` or `class`, set a `click` **event listener** on the `button`, use an `arrow function` to **_return_** a `call` to the `getData()` **function** **_inside it_**, and then **optionally** use `CSS in JS` to **change** the **_look_** of the **page** when the `data` is **_rendered_**. I do that with **_my_** `OMDB Api` **movie application**, for example.

This is how I `query` my `Get Movie Info` **button** by `id`, and `set` the `click event listener` **_on it_**:

```js
const button = document.getElementById("btn");
button.addEventListener("click", () => {
  getData();
  document.getElementById("container").style.border = `2px solid #000`;
});
```

I do it **_this way_** because I have **_more than_** **one line** **_inside_** the `body` of the `arrow function`. Since I do, I make an **actual call** to the `getData function`. In the line **_following_** that **call**, I `query` my `div` **tag/element** with the `id` of `"container"` and **_set_** the **CSS in JS** `style.border` **property** on it to `2px solid #000`. If I could **_fit_** **everything** on **_one line_**, meaning that I did **_not want_** to **change** the **look** of the **_page_** when I have `retrieved` the `data` from the `OMDB Api` after the `click event` has been **_fired_**, my `JavaScript` **code** would look something like **_this_**:

```js
const button = document.getElementById("btn");
button.addEventListener("click", getData);
```

This is how my `Movie Information` page looks like **_before_** I **retrieve** a `movie by title`:

![OMDB Api home page before query](images/Screenshot-2020-03-22-15.18.18.png)

And this is how it **looks** like **_after_** `data` **retrieval**:

![OMDB Api home page after query](images/Screenshot-2020-3-22-15.20.04.png)

Have **_fun_** with this. Be **creative**. You do **_not_** **have** to **use** the **_same_** `query parameters` I **did**. You **_do_** still have to **use** your `api key`. **_Without it_**, you **_won't_** be able to get **_any data_**! But you do **_not_** **have to use** the `movie title parameter`, `t`. You can use something else! And make the `page layout` and `styling` your **_own_**!

### Week 8 Homework Part 2:

1. What does `AJAX` **_stand_** for?

2. What does `XML` **_stand_** for?

3. What `object` does `AJAX` **_use_** to **request** `data` from the `server`?

4. What is the **special feature** of `AJAX` that makes `developers` **_like_** to work with it? **Hint:** It has to do with enhancing the **User Experience** (**UX**).

5. Explain the basic **five steps** **_involved_** in the **execution** of an `AJAX XMLHttpRequest` between the `browser` and the `server`.

6. What makes up the **core** of `AJAX`?

7. What is the `XMLHttpRequest Object` **_used_** for?

8. What is the **syntax** for `XMLHttpRequest()`?

9. Give me an **_example_** of `XMLHttpRequest()`. Use your **project code** please.

10. What **_must be_** **called** before **_any other_** **method** **calls** and **_why_**?

11. In the `OMDB Api project`, even though the `OMDB Api` is **_served_** over `http`, we use `https`. Why?

12. What keyword is used to initialize the XMLHttpRequest object?

13. What does `new XMLHttpRequest()` **_create_**?

14. What are the **5 things** that the `new` **keyword** does?

15. **_Using code_** from your **project**, give me an example of `this` being **returned** due to the **use** of the `new` **keyword** with `XMLHttpRequest()` to **_create_** an `instance` of the `XMLHttpRequest Object`.

16. Describe what the `XMLHttpRequest.open()` **method** **_does_**.

17. **_Using code_** from your **project**, give me an **example** of `XMLHttpRequest.open()`.

18. Tell me what the **values** **_passed_** to the `open()` **method** are for, and give me the **parameters** they **_represent_** the **values** (aka `arguments`) of. **Hint:** **_part_** of the **answer** may **_reside_** in the `slide deck` and **_inside_** the `Related Resources` **links** at the end of the deck, and **part** will **_reside_** in the `README.md` of the `week 8 homework repository`. You **_will have_** **come across** the **information** while **_reading_** the **instructions** for going through the **steps** of **_building_** your **project**.

19. **Using code** from your **project**, give me an **example** of `XMLHttpRequest.send()`.

20. Tell me if there are **_any_** **values** **_passed_** to our `send()` **method**. What **_optionally_** **could** be **_passed_** to the **method**, and why do we NOT have to **pass** this `optional parameter/argument` to **_our_** `send()` **method**?

## Related Resources:

- [AJAX Introduction: W3Schools](https://www.w3schools.com/xml/ajax_intro.asp) - `W3Schools` **_contains_** a `complete tutorial` on `AJAX` with **live exercises** **_available_** for you to play with. They basically have **everything** `JavaScript related` on their site.

- [OMDB API: The Open Movie Database](http://www.omdbapi.com/)

- [JSON.parse(): W3Schools](https://www.w3schools.com/js/js_json_parse.asp)

- [Getting movie data from OMDB API using fetch(): Medium.com](https://medium.com/@cferreirasuazo/getting-movie-data-from-omdbapi-using-fetch-f2b96ae230dd) - **_not meant_** for you to `switch` to **using** `fetch()` for **_this project_**, but so you can **learn more** about the `OMDB Api` **url** and **_how_** to **query** `data` with it. It's **_just another_** **place** to get **_more information_** and a `visualization` of the `Api` **implementation**, along with the `OMDB Api` **documentation**, my `slide deck`, and the `homework` **documentation** **_here_**. It's for those of you who are **interested** in **_learning more_**, and perhaps even want to `customize` the `data retrieval` to `match` your **_interests_**!

- [Dynamic Web 1: Using AJAX With Apis (OMDB movie Api): Github gh-pages](https://interglobalmedia.github.io/dynamic-web-1-omdb-api-ajax/#/)
