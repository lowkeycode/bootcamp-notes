# Bootcamp Notes

## Font-size

Setting font size to 62.5% sets it to 10px, instead of default 16px. Then rems multiply off it. We make it a percentage instead of a solid 10px so users can zoom in and out and the font will scale accordingly.

There is an increasing recommendation to have no fonts on a website smaller than 18px for accessibility reasons.

18/16 = 1.125 or 112.5%

To make the math easier when using rems just do 20px

20/16 = 1.25 or 125%

## Calc

Using calc() when working with different units can be a lifesaver

```css
.text-content,
.img-content {
  float: left;
  width: 60%;
}

.img-content {
  width: calc(40% - 40px);
  margin-right: 40px;
}
```

## CSS Display Property

- Elements set to display block will take up the whole width of the page

- Inline elements only take up enough space for the content

- Inline block sets ghosts space between elements as it then treats them like they are text(words) and try to put space in between

## Anchor tags

- Are by default inline and can have very quirky effects

- Ensure to display inline block or block to avoid weird padding or margin issues (which can also affect alignment) especially when nested inside of another element

- Again keep in mind anchor tags have quirky effects

## Images

Its helpful to put a max-width: 100% on images to make sure they do not flow outside their parent. Consider also making the images parent be a percentage of it's parent container for good responsive images in some cases but can scale images down in size fairly quickly

- For the love of god don't forget to display: block or overflow: hidden if the image has extra white space between it and its container

## CSS Pseudo Selectors

- when using the child selectors ex.) first-child if there is a sibling element that is not the same type of element then no styles will be applied. Instead use :nth-of-type.

```html
<section>
  <h1>This is a title</h1>
  <p>This is the first sentence</p>
  <p>This is the second sentence</p>
  <p>This is the third sentence</p>
  <p>This is the fourth sentence</p>
</section>
```

```css
/* Style Not Applied */
section p:first-child {
  color: red;
}

section p:last-child {
  color: blue;
}

section p:nth-child(3) {
  color: pink;
}

/* Style Applied */
section p:nth-of-type(1) {
  color: red;
}
```

## CSS Pseudo Elements

The ::before and after elements are by default inline elements. We can adjust them like text to increase their size with font-size. If we want to change the height of the element we need to make it either inline-block or a block level element then adjust the height

```css
.name::before {
  content: "☃🥶";
  height: 50px;
  display: block;
}
```

If you want a hover effect it needs to be :hover::after NOT ::after:hover
For accessibility make sure to use :focus as well.

```css
a:focus::after,
a:hover::after {
  background: rgba(137, 43, 226, 0.4);
}
```

## Navigation Accessibility

Add an a tag to the top of the page and hide it with css

```css
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  margin: -1px;
  border: 0;
  padding: 0;
  white-space: nowrap;
  clip-path: inset(100%);
  clip: rect(0 0 0 0);
  overflow: hidden;
}
```

We can also show it if we want on :focus

## Navigation Dropdowns

Use height: 0; overflow: hidden; instead of display none for SEO and accessibility.

## Test 1: HTML/CSS Topics

- Folder/Project organization best practices
- Media query best practices
- Rems
- Accessibility best practices
- Semantic elements
- The box model
- CSS calculations
- Color
- Positioning, flexbox, floats (no grid)

## SASS (Pre-processors)

SCSS is different from SASS in that CSS is also valid SCSS so you can combine the two and use as much or as little as you like.

SCSS compiles into CSS, so when linking the style sheet it must be the compiled CSS stylesheet

With the live sass compiler extension then we create a new directory inside our root folder called .vscode. Then we make a settings.json file and put the following inside.

```json
{
  "liveSassCompile.settings.formats": [
    {
      "format": "expanded",
      "extensionName": ".css",
      "savePath": "/styles"
    }
  ],
  "liveSassCompile.settings.excludeList": ["**/node_modules/**", ".vscode/**"],
  "liveSassCompile.settings.generateMap": false,
  "liveSassCompile.settings.autoprefix": ["> 1%", "last 2 versions"]
}
```

Then we make a styles directory. Then we make a sass folder inside the styles folder.

A short cut to add inside files we can use relative paths. mkdir styles/sass from the styles folder.

If live sas is not compiling make sure to check the live sass's settings.json and set the following to null

```json
"liveSassCompile.settings.includeItems": null,
```

## Git & Github

Git is the version control system on your local machine. Github is cloud storage for repos.

We can check our commits with git log.

```
commit e5618b7ea787b913b386f3e6dac7387a7d902a0a (HEAD -> master)
Author: lowkey <saltyndea@gmail.com>
Date:   Mon Aug 30 14:43:48 2021 -0600

    Added style sheet

commit 5587e2b57a2c97d8e719661dc31053db54bee6b0
Author: lowkey <saltyndea@gmail.com>
Date:   Mon Aug 30 14:39:36 2021 -0600

    babys growin

commit 20bbe41db42d62ea79f98269fad6255d175f5504
Author: lowkey <saltyndea@gmail.com>
Date:   Mon Aug 30 14:31:51 2021 -0600

    :rocket:
(END)

```

## Time Travel

To check out a previous commit use git checkout.

```
git checkout 20bbe41db42d62ea79f98269fad6255d175f5504
```

This creates a detached HEAD state. Our old version of our code is then displayed in our code editor.

We are also in a copy head.

Ashleys-MacBook-Air.local~/Documents/lowkey/juno/bootcamp/week-2/testy-git lowkey master~2ƒ𝑥

So we checkout the main branch (or master in this case because of the switch o ver.) After any changes we need to make then checkout to reattch the head to the present master directory.

git checkout master

Then we can hook up our github by starting a repo and copying the https url and set the remote origin.

git remote add origin https://github.com/lowkeycode/testy-git.git

We can check if this is properly set

git remote -v

Which returns:

origin https://github.com/lowkeycode/testy-git.git (fetch)
origin https://github.com/lowkeycode/testy-git.git (push)

Then we push to github
git push origin master

Note: all following repos should be set to main as I updated the global default setting

AZALIA's error code (Which I've gotten before)

main (non-fast-forward)
error: failed to push some refs to 'https://github.com/azalialoe/baby-bye-bye-bye.git'
hint: Updates were rejected because a pushed branch tip is behind its remote
hint: counterpart. Check out this branch and integrate the remote changes
hint: (e.g. 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

A hack is to git push -f origin main but is really bad as it will overwrite anything on origin and any work other people have done.

## Flexbox

flex property:

Is short hand for

- flex-grow
- flex-shrink
- flex-basis

Flex grow is what we do by default to grow items to take up extra space starting after its defined width. Default is 1. This property creates a ratio and how its distributed between the flex items in relation to each other. The default 1 gives each item 1 unit of "space". The higher the number Ex.) flex-grow: 4; applied to a given item will make that item grow at 4x compared to other items that will only get 1 unit of "space".

Flex shrink says if there is not enough space available where do we take the space from. Usually not used often as most of the time you don't really want content to shrink and would rather have it wrap to the next line.

Flex-basis auto means setting width to the content. Or we can use it to set the width of the items to whatever we want.

## Forms

Checkbox hack

```css
input[type="checkbox"] {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  border: 1px solid red;
  height: 12px;
  width: 12px;
  display: block;
  margin: 0 10px;
}
input[type="checkbox"]:checked::before {
  content: "✚";
  color: blue;
  display: block;
  font-size: 10px;
  line-height: 12px;
}
```

Dropdown hack

appearance none and absolute position an background image...I think?

I'm having trouble empowering web-enabled schemas when integrating cross-platform paradigms with flexbox.

## Git Branching

Please see bootcamp notes for any clarifications!

A branch is a copy of your last committed pushed code to github.

Initializing:

1. git init
2. Create a repo on git hub & copy the url
3. git remote add origin https://github.com/lowkeycode/git-branching-lesson.git
4. git add -A
5. git commit -m "commit message"
6. git branch -M main
7. git push origin main

Branching:

git branch (shows all branches and your current branch)

Create new branch if it doesn't exist (also changes current branch Ex.) git checkout main)

1. git checkout -b branch-name

This only creates the branch on the local machine

When switching branches if you need to go work on another branch you will want to use a git stash

git stash then git checkout another-branch and after you move back you can do git stash apply to get your changes out of the stash again (not used often)

2. Add then commit then push: (ACP)

Push with git push origin {branch name} to create a new branch on github

Merging:

There is a built in way in github - Pull requests. We won't touch pull requests until later
On the command line:

git branch to know which branch your on before merging

When merging into a branch you want to be IN THAT BRANCH ex.) if you want to merge a branch into main, go into the main branch

git checkout main

Then you want to make sure everything is up to date in case other people have made pushes to main

git pull origin main

git merge {branch name}

Merging does not require adding or committing (you can see this by checking git status)

git status

git push origin main

Deleting:

The branch still exists after merging so we should clean it up if no longer needed. Keep in mind that the branches exist bot on our machine in git AND on github, so we need to delete both.

Make sure you ARE NOT in the branch your going to delete.

Delete github branch
git push origin :branch-name

Delete local git branch
git branch -d branch-name

## Github Pages From Command Line

Create a folder and git init
git remote add origin ORIGIN
git branch -M main

Then create a branch called gh-pages
git checkout -b gh-pages
git push origin gh-pages

## Syncing Pages

In main

git merge gh-pages

git push origin main

## Unzip From Command line

unzip filename.zip -d directoryToUnzipInto

Without the -d flag it with unzip in current working directory

## Javascript

## Truthy / Falsey

null : falsy
undefined : falsy
any string : truthy
an empty string : falsy
the number 0 : falsy
any number higher or lower than 0 : truthy

## Functions

- Functions are FIRST CLASS CITIZENS which means they are just values

Function Declartion:

- Hoisted

```js
function helloWorld() {
  console.log("Hello World");
}
```

Function Expression:

- The definition of a function stored in a variable
- An anonymous function stored in the variable
- Not hoisted

```js
const helloWorld = function () {
  console.log("Hello World");
};
```

## Objects

There are 2 ways to access properties in objects. Dot notation or bracket notation.

```js
const clothing = {
  belt: "Can't member",
  socks: 34,
  shoes: 2,
  pants: 3,
  hat: true,
  tshirts: {
    sml: 3,
    med: 4,
    lrg: 10,
  },
};

clothing.socks;
// 34

clothing["shoes"];
//  2

const userChoice = prompt("What item do you want to know about?");
//  The user picks shoes, so now we have the string "shoes"

clothing[userChoice];
// 2
```

Dot notation is easiest and easiest to remember. However it cannot use variables to access objects. Ex.) clothing.userChoice will NOT work

Bracket notation has good use cases though is harder to remember. The value inside the brackets need to be in a string or a variable that contains a string matching the property name.

Both can access nested levels.

clothing.tshirts.sml
clothing["tshirts"]["sml"]

You can mix and match as well.

clothing.tshirts[userChoice]

To loop over objects you can use a for in loop

```js
const clothing = {
  socks: 34,
  shoes: 2,
  pants: 3,
};

for (let item in clothing) {
  console.log(`I have ${clothing[item]} ${item}`);
}
```

## Git Collaboration

Create a feature branch

git checkout -b feature

Then add changes, and add, commit then push to feature branch name

On git hub in that repo you get "Compare & pull request"
Click that to open a new pull request

If after making multiple pushes to the feature branch, click the pull requests tab at the top and click new pull requests and pick the proper branch to merge into main

Then on the open pull request page double check at the top left what branch you are merging which branch into. Rarely need to change this but good to double check.

Then click merge pull request

Then you can click the files changed tab to review code and the review changes button there is where one would approve, request changes or comment on the pull request.

Then click merge pull request and confirm. Then you can delete the branch on github to clean up (click on the branches drop down and click view all branches and click the garbage can beside the branch to delete)

Then we git checkout main and git pull to get the updates down from github.

git pull origin main

Then clean up the feature branch on local if you'd like (Not neccessary but may cause clutter if not deleting unused branches)

Delete github branch
git push origin :branch-name

Go to main branch
git checkout main

Delete local git branch
git branch -d branch-name

## Git Conflicts

Check the notes, This part of the lesson didn't work properly and moved very fast.

## Github Organizations

Click plus sign at top right of github to create an organization and go through the steps.

Then git clone the url of the repo in that organization

git clone https://github.com/cameronremesz/testy.git

## Array Methods - Code Along

Namespacing is also helpful in 2 ways. First, if we use the init method then all the previous code is parsed and defined in the global execution context then called once. This gives a small performance boost. Second, it also makes debugging easier as you will have the separation of an error being thrown while parsing (when we define it) or in execution AFTER calling the init method.

## APIs

We can elgantly add search params by using the URL & URLSearchParams constructors, passing the URL our api url and the search params an object of search params then calling fetch with the endpointUrl variable.

```js
const endpointUrl = new URL("https://www.septastats.com/api");

endpontUrl.search = new URLSearchParams({
  ml: "salad",
});

fetch(endPointUrl)
  .then((response) => {
    return res.json();
  })
  .then((data) => {
    console.log(data.data);
  });
```

## Promises

```js
const request = fetch("https://restcountries.eu/rest/v2/name/canada");
console.log(request);
// Promise {<pending>}
```

Here we log the response and we get a Promise (Pending)

Promises can be fulfilled or rejected but the act as a place holder object until the data comes back. It holds place for a future value that we know will be returned whether it comes back with our data or for whatever reason encounters an error Ex.) The server holding our data is down.

This allows our code to keep running while the fetch happens.

Whats the big advantage?
They allow the ability to chain asynchronous operations.

Lifecycle:

Promises can be in different states.

In the beginning it is pending.
Then when it has finished it is settled.
Settled promises can be fulfilled or rejected.

fetch() returns a Promise.

On ALL Promises we can call the then method.

```js
const request = fetch("https://restcountries.eu/rest/v2/name/canada");
console.log(request);

const getCountryData = function (country) {
  fetch(`https://restcountries.eu/rest/v2/name/${country}`).then();
};
```

The .then() method gets a callback that is executed as soon as the Promise is settled.

This function receives one argument which is the resulting value of the settled Promise - usually called response (response)

```js
const getCountryData = function (country) {
  fetch(`https://restcountries.eu/rest/v2/name/${country}`).then(function (
    response
  ) {
    console.log(response);
    // Response
  });
};

getCountryData("canada");
```

The data we want though is now in the body of the Response. To parse this data we need to call .json() on the Response which will parse the data out of the body for us.

```js
const getCountryData = function (country) {
  fetch(`https://restcountries.eu/rest/v2/name/${country}`)
    .then(function (response) {
      console.log(response);
      response.json();
    })
    .then(function (data) {
      console.log(data);
      // Our API data shows up here
    });
};

getCountryData("canada");
```

To error handle we use a .catch() method to catch any errors that may be thrown in the chain.

```js
const getCountryData = function (country) {
  fetch(`https://restcountries.eu/rest/v2/name/${country}`)
    .then(function (response) {
      console.log(response);
      response.json();
    })
    .then(function (data) {
      console.log(data);
      // Our API data shows up here
    })
    .catch(function (error) {
      console.log(error);
    });
};

getCountryData("canada");
```

<!-- ! This is additional -->

The json() function is also an async function so it also returns a Promise. So we need to return the response.json() so we can handle the second Promise with a second .then() method which gives us a callback that handles the resolved value of response.json() which is our data.

With arrow functions this is simplified because if with a one liner you can automatically return the values in the callbacks.

```js
const getCountryData = function (country) {
  fetch(`https://restcountries.eu/rest/v2/name/${country}`)
    .then((response) => response.json())
    .then((data) => console.log(data));
};

getCountryData("canada");
```

Handling Promise errors:

These are rejected promises. Errors propogate down the chain so even when using multiple fetch methods if any error is thrown in ANY of the fetch methods we can catch that error at the end with a .catch() method. (Again receives a callback that we can use to define what we do on error. Inside this call back is where you would call a function we define to display an error message). This error is an object so we can access the message instead of rendering the error object.

```js
const getCountryData = function (country) {
  fetch(`https://restcountries.eu/rest/v2/name/${country}`)
    .then((response) => response.json())
    .then((data) => console.log(data))
    .catch((err) => console.log(err.message));
};

getCountryData("canada");
```

If we call the getCountryData() method with a property the server still checks for that value and even though it doesn't find it it is a fulfilled promises with a status of 404 and ok set to false

```js
const getCountryData = function (country) {
  fetch(`https://restcountries.eu/rest/v2/name/${country}`)
    .then((response) => response.json())
    .then((data) => console.log(data))
    .catch((err) => console.log(err.message));
};

getCountryData("adfsgsdfgsd");
```

We have to reject this ourseleves manually by throwing our own error in the first then() callback. We define out own message to throw. When we throw our own error the Promise IMMEDIATELY rejects and we can then use in the .catch() method. This allows us to write customer error messages using the response status which is more user friendly.

```js
const getCountryData = function (country) {
  fetch(`https://restcountries.eu/rest/v2/name/${country}`)
    .then((response) => {
      if (!response.ok) {
        throw new Error(`Country not found! ${response.status}`);
      }

      return response.json();
    })
    .then((data) => console.log(data))
    .catch((err) => console.log(err.message));
};

getCountryData("adfsgsdfgsd");
```

In our fetch function (either async or promised based with .then()), we can just return the data after it's parsed from the .json() method.

Anything returned from an async function IS A PROMISE. So below we'd expect the returnedData to be our resolved api object but its actually a promise.

```js
const getPokemon = async function (url) {
  try {
    const res = await fetch(url);
    const data = await res.json();
    console.log(data);
    //  Object
    return data;
  } catch (error) {
    console.log(error);
  }
};

const returnedData = getPokemon("https://pokeapi.co/api/v2/pokemon/1");
console.log(returnedData);
//  Promise <pending>
```

## Error Handling

In our .then() method we want to deal with any errors that may happen so we can a .catch() method and manually throw the error and then catch it in the .catch()

```js
const pokemonURL = "https://pokeapi.co/api/v2/pokemon/1123456789/";

fetch(pokemonURL)
  .then((res) => {
    if (res.ok) {
      return res.json();
    } else {
      console.log("Im fired");
      throw new Error("Custom error message");
    }
  })
  .then((jsonData) => {
    console.log(jsonData);
  })
  .catch((err) => {
    console.log(err.message);
  });
```

## this Keyword

Why?

Because the developers who wrote javascript needed to be able to write the methods like .push(). When they were writing the method on the Array object they had to have a way of saying what exactly to appended the pushed value to. Alas, this.

## Firebase

1. Setup project on firebase.
2. Add realtime db
3. Add setup snippets and script tags from firebase
4. Initialize db
5. Create reference to db
6. CRUDL db with set update and on

## Modules

Fun fact: ESModules don't work without a live server, you will get a CORS error. Never ran into it before because I've always had live-server

Check your notes on named/default imports/exports

## React

- JSX can only return one element, no siblings
- JSX html elements are just values so we can store them in variables
- Inside the return statement we cannot use if statements because they are statements and do not evaluate to anything. We need to use an expression. Like a ternary operator. This is similar to template literals in JS.

SASS with React:

- npm install node-sass
- if errors follow trouble shooting steps in command line

## Components

- When we are looping over things we need to make sure we return something so .map is used instead of .forEach

- When returning (Ex.) inside a map function), to get a multi line return you need to use () after the return. One liners don't need it. return()

```js
function App() {
  console.log(animals);

  return (
    <div className="App">
      <h1>Manimals</h1>

      {animals.map((animal) => {
        return (
          <div className="pet">
            <h2>{animal.name}</h2>
            <p>Type: {animal.type}</p>
            <p>Size: {animal.size}</p>
            <img src={animal.picture} alt={`An adorable ${animal.type}`} />
          </div>
        );
      })}
    </div>
  );
}
```

.map() returns an array but JSX treats arrays in a different way so returning one is completely valid. JSX sees an list of JSX elements and will render them. This is how react is by design, it wants us to map over arrays.

React keeps track of every single element in the DOM. So in our arrays (lists) it wants us to number them with a KEY so react can find it really quickly

It may be intuitive to use the index when looping over to use as the key. But this is incorrect and if the list size changes the keys may change for any given elements

Most apis or databases will provide a universal unique id UUID, or we can use an npm package to create these for us. We should use those in professional projects, in practice apps without any of these then we can just use the index because YOLO.

```js
animals.map((animal, i) => {
  return (
    <div className="pet" key={i}>
      <h2>{animal.name}</h2>
      <p>Type: {animal.type}</p>
      <p>Size: {animal.size}</p>
      <img src={animal.picture} alt={`An adorable ${animal.type}`} />
    </div>
  );
});
```

We can put our map in its own component making sure we import the animals data for it to use and then we can reuse this component anywhere in our app

```js
import animals from "./animals";

const PetList = () => {
  return (
    <div>
      {animals.map((animal, i) => {
        return (
          <div className="pet" key={i}>
            <h2>{animal.name}</h2>
            <p>Type: {animal.type}</p>
            <p>Size: {animal.size}</p>
            <img src={animal.picture} alt={`An adorable ${animal.type}`} />
          </div>
        );
      })}
    </div>
  );
};

export default PetList;
```

## Events

With events in react we just put the event listener directly on the element we are defining and can write our callback then just pass it into the react event attribute (Ex.) onClick)

```js
function App() {
  const handleClick = () => {
    console.log("clicked");
  };

  return (
    <div className="App">
      <h1>Events</h1>
      <button onClick={handleClick}>Make clicks, not war</button>
    </div>
  );
}
```

- Side note - We can write statements in JSX. just not in the return statement in jsx. Above the return statement you CAN write regular js like control flow etc.

## Props

We can pass props (properties) to our components and then access the props object from inside th component by destructuring or saying props.whateverPropIWannaAccess

The key prop is specifically only used by react and is used for providing each rendered component with a unique ID

We also have access to children props if we pass jsx elements or even another component inside a component

```js
import FanInfo from "./FanInfo";
import "./App.css";

function App() {
  //  Data from an API call or db
  const listOfTeams = [
    "Toronto Ancient Birbs",
    "Los Angeles Tankers",
    "Miami Warmths",
    "Edmonton Dinosaur Juice",
  ];

  const followTeam = () => {
    console.log("Following Team");
  };

  return (
    <div className="App">
      <h1>Sports</h1>

      {listOfTeams.map((team, i) => (
        <FanInfo teamName={team} key={i} subscribe={followTeam}>
          <h3>Writing inside a component</h3>
          <p>Lorem ipsum dolor sit amet.</p>
        </FanInfo>
      ))}
    </div>
  );
}

export default App;
```

```js
const FanInfo = ({ teamName, subscribe, children }) => {
  console.log(children);
  return (
    <div>
      <h2>Welcome to the arena of the {teamName}</h2>
      <button onClick={() => subscribe(teamName)}>Tell Me More!</button>
      {children}
    </div>
  );
};

export default FanInfo;
```

## State

```js
let [counter, setCounter] = useState(0);

const handleClick = () => {
  setCounter(counter++);
  console.log(counter);
};
```

This will not work because we are not actually updating our state but rather reassigning the variable of counter which cause some whacky ass behaviour. Some shorthand JS syntax in react can fuck shit up.

## useEffect

useEffect mimics the functionality of componentDidMount, componentWillUnmount etc. A component renders on page load and any time it changes state.

```js
import { useState, useEffect } from "react";

import "./App.css";

function App() {
  const [loggedIn, setLoggedIn] = useState(false);
  const [userName, setUserName] = useState("Cameron Remesz");

  useEffect(() => {
    console.log("mounted");
  }, [loggedIn]);

  return (
    <div>
      <h1>Welcome to the fuckin' party</h1>
      <button onClick={() => setLoggedIn(!loggedIn)}>
        {loggedIn ? "Log out" : "Log in"}
      </button>

      {loggedIn ? (
        <p>Time to party, {userName}</p>
      ) : (
        <p>Please log in so you can party</p>
      )}

      <button onClick={() => setUserName(userName + "☠️")}>
        Add ☠️ to User name
      </button>
    </div>
  );
}

export default App;
```

useEffect takes a callback function to run when state changes and a second argument of an array of pieces of state to track and run the callback on render. This lets us target only specific components

Conditional rendering listening to a specific piece of state with useEffect

```js
useEffect(() => {
  loggedIn ? setUserName("Cameron Remesz") : setUserName("");
}, [loggedIn]);
```

To get a component to only run once on mount you pass it an empty array.

```js
useEffect(() => {
  fetch(`https://8ball.delegator.com/magic/JSON/Am I going to be rich?`)
    .then((res) => res.json())
    .then((data) => setEightBall(data.magic.answer));
}, []);
```

If you leave a useEffect with no array and no conditional it will create an infinite loop as useEffect by default listens to any render of any piece of state

There are instances when you want to use useEffect without the dependencies array but they are edge casey => google if needed

For unmounting there are instances we want to do something. For example a subscription to a data base and when we log out we need to turn off that subscription otherwise data is still flowing and going nowhere. This is called a memory leak.

We mimic a componentWillUnmount with passing a returned function with whatever we want to do on unmount

```js
import { useEffect } from "react";

const VipRoom = () => {
  useEffect(() => {
    console.log("connected to firebase with .on()");

    return () => console.log("component unmounted");
  }, []);

  return (
    <div>
      <h2>Hello</h2>
      <p>Welcome to the VIP room</p>
    </div>
  );
};

export default VipRoom;
```

## Deploying React With Netlify

Using variables that are not used later in the code will cause Netlify to fail on build but will give you a stack trace from its terminal when you click on that specific deploy.

## Note On Forms

For setting the default value of a drop down (or some other inputs) we use a set state setting it to the value of our place holder (whatever we choose to name it) Then set the select value to that so it shows our disabled value first prompting the user to pick one then all our options get their corresponding value property. Remember all form inputs need a value property for react to keep track of them properly.

```js
import { useState } from "react";

const PhotoForm = () => {
  const [userChoice, setUserChoice] = useState("placeholder");

  return (
    <form>
      <h2>Show me some photos that are:</h2>
      <select name="photoOrientation" id="photoOrientation" value={userChoice}>
        <option value="placeholder" disabled>
          Pick One
        </option>
        <option value="square">Square</option>
        <option value="portrait">Portrait</option>
        <option value="landscape">Landscape</option>
      </select>
      <button type="submit">Give me the photos!!!</button>
    </form>
  );
};

export default PhotoForm;
```

## Updating State From A Child

If we need to access parent state from a child we define a function on the parent utilizing the updating state method somewhere inside and accepting a parameter that will be passed in once executed in the child component.

```js
// App.js
import axios from "axios";
import { useState, useEffect } from "react";

import DisplayPhotos from "./DisplayPhotos";
import PhotoForm from "./PhotoForm";

import "./App.css";

function App() {
  const [allPhotos, setAllPhotos] = useState([]);
  const [filteredPhotos, setFilteredPhotos] = useState([]);

  useEffect(() => {
    axios({
      url: "https://api.unsplash.com/search/photos",
      method: "GET",
      dataResponse: "json",
      params: {
        client_id: "KVIMQR520-tf2c7YpYmdKZDQd-jvgDSXVvQfNpS2n9c",
        query: "puppies",
        per_page: 30,
      },
    }).then((res) => {
      const poopyPics = res.data.results;
      const withOrientation = poopyPics.map((photo) => {
        const ratio = photo.width / photo.height;

        let orientation = "square";

        if (ratio < 0.75) {
          orientation = "portrait";
        } else if (ratio > 1.35) {
          orientation = "landscape";
        }

        return { ...photo, orientation: orientation };
      });
      setAllPhotos(withOrientation);
    });
  }, []);

  const getPhotos = (e, userChoice) => {
    e.preventDefault();
    const copyOfAllPhotos = [...allPhotos];
    console.log(copyOfAllPhotos);

    const photosByOrientation = copyOfAllPhotos.filter((photo) => {
      return photo.orientation === userChoice;
    });

    setFilteredPhotos(photosByOrientation);
  };

  return (
    <div className="App">
      <h1>Show me the poopies!</h1>
      <PhotoForm getPhotos={getPhotos} />
      <DisplayPhotos photos={filteredPhotos} />
    </div>
  );
}

export default App;
```

```js
// PhotoForm.js
import { useState } from "react";

const PhotoForm = ({ getPhotos }) => {
  const [userChoice, setUserChoice] = useState("placeholder");

  const handleUserChoice = (e) => {
    setUserChoice(e.target.value);
  };

  return (
    <form
      onSubmit={(e) => {
        getPhotos(e, userChoice);
      }}
    >
      <h2>Show me some photos that are:</h2>
      <select
        name="photoOrientation"
        id="photoOrientation"
        value={userChoice}
        onChange={handleUserChoice}
      >
        <option value="placeholder" disabled>
          Pick One
        </option>
        <option value="square">Square</option>
        <option value="portrait">Portrait</option>
        <option value="landscape">Landscape</option>
      </select>
      <button type="submit">Give me the photos!!!</button>
    </form>
  );
};

export default PhotoForm;
```

## Project Management

1. Design
2. Develop
3. Analyze
4. Evaluate

### Design

- Gather project requirements
- Discuss schedules, strengths & weaknesses
- Define roles and responsibilities
- Define MVP & stratch goals
- Create the plan

Project requirements:

- Discuss client brief (What are you building? Make sure everyone is on the same page. Some people get different takeaways from client briefs)
- Who is your audience/user? What must it do? What are the stretch goals? Does everyone understand the Deliverables

Understanding your team:

- Hash out coinciding schedules
- Discuss strengths/weaknesses & room for growth

Define roles & responsibilities:

- Define how decisions will be made as a group

Define MVP & stretch goals:

- Self explanatory

Creating the plan:

- Consider project management tool like asana, jira or trello to track and keep a pulse on the project
- Discuss touch points/standups (when you'll meet up)

### Develop

Communication:

- Commit to touch points & communication streams & keep to them
- Documents decisions

Conflict resolution:

- People thinking different things and not being able to resolve things immediately
- This is good. Discuss feelings and then agree on a solution and then commit.

### Analyze

### Evaluate

- Retrospective meetings (What went well? What didn't? What to do differently? )

## Routing


Routes are components used for conditional rendering


We wrap our Router around our whole app component then we can use routes inside it.

```js
import { BrowserRouter as Router, Route, Link } from "react-router-dom";

import Catalogue from "./Catalogue";

function App() {
  return (
    <Router>
      <div className="wrapper">
        <header>
          <h1>Hark Flarks</h1>
        </header>

        <Route exact path="/">
          <Catalogue />
        </Route>
      </div>
    </Router>
  );
}

export default App;

```
The below throws a warning because useEffect is pissed off that the movieId variable that we use in the url isn't inside of the useEffect so it can't keep track on it and what its value is on each render. So we put it inside the dependency array. This is ok because when the movieId is initially set when the component mounts it will cause a render on mount just as before with an empty array.

We know that the value destructured into movieId won't change, but we need to hold useEffects hand and point it at that value so it doesn't get it's wires crossed.


```js
import { useParams } from 'react-router-dom';
import { useState, useEffect } from 'react';
import axios from 'axios';

const MovieDetails = () => {

  const { movieId } = useParams();

  const [movie, setMovie] = useState({});

  useEffect(() => {
    axios({
      url: `https://api.themoviedb.org/3/movie/${movieId}`,
      params: {
        api_key: 'fe2050bd37a28bdbe4179a065be4bb54'
      }

    })
    .then(res => {
      console.log(res.data)
      setMovie(res.data);
    })
  }, [])

  return (
    <h2>Deets</h2>
  )
}

export default MovieDetails
```

We resolve this by passing the movieId into useEffect

```js
const MovieDetails = () => {

  const { movieId } = useParams();

  const [movie, setMovie] = useState({});

  useEffect(() => {
    axios({
      url: `https://api.themoviedb.org/3/movie/${movieId}`,
      params: {
        api_key: 'fe2050bd37a28bdbe4179a065be4bb54'
      }

    })
    .then(res => {
      console.log(res.data)
      setMovie(res.data);
    })
  }, [movieId])

  return (
    <h2>Deets</h2>
  )
}
```



The Link tag sets the url so then when the url bar is updated the Movie details component is rendered in the /movie:movieId route which we steal off useParams and use that id to make the second request

```js
import { useState, useEffect } from "react";
import axios from 'axios';
import { Link } from 'react-router-dom';

const Catalogue = () => {

  const [movies, setMovies] = useState([]);

  useEffect(() => {
    axios({
      url: 'https://api.themoviedb.org/3/discover/movie',
      params: {
        api_key: 'fe2050bd37a28bdbe4179a065be4bb54',
        language: 'en-US',
        sort_by: 'popularity.desc',
        include_adult: 'false',
        include_video: 'false',
        page: 1,
        primary_release_year: 1999,
      },
    })
    .then(res => {
      setMovies(res.data.results);
    });
  }, [])

  return (
    <ul className="catalogue">
      {
        movies.map(movie => {
          return (
            <li key={movie.id}>
              <Link to={`/movie/${movie.id}`}>
                <img 
                src={`https://image.tmdb.org/t/p/w500/${movie.poster_path}`}
                alt={`Poster for ${movie.original_title}`} 
                />
              </Link>
            </li>
          )
        })
      }
    </ul>
  )
}

export default Catalogue

```

## Custom Hooks

Custom hooks are used as more of a part of the iterative refactoring process when there is lots of code. Try not to use too early on or the code can become convoluted and harder to even read.

## Tech Challenges

Tech challenge prep:

Adrian

Cover basics:
- loops how they work, which solution is best
- Use code wars to stay sharp
- Relax, slow things down, think things through before talking and deliver like normal conversation (casually), tell them what your thinking
- In thank you email ask for feedback at that point (can be hit and miss if you'll get any back)


Safi
- Focus on basics and what you know really well so you have confidence when speaking about them
- Interviewers will push until you get on a topic you don't know and to get you to talk about things you don't know
- How will you approach being asked something you don't know (being honest and saying that you don't know about it yet) "This is outside of the realm of the web development that I’ve learned about up until now."
- Are you someone they'd wanna work with? Be yourself and talk about it as yourself and don't come across as a robot
- Ask for clarification or ask for time to think about it if you need it
- Ask questions for clarification (this shows trying to get a deeper understanding of the question at hand)
- The goal of tech interviews is not to get every question right but rather your relationship to code and the people who work with the team
- If a company seems sketchy post about it in Juno slack and it will be quickly crowd source detected as a fraud or not
- Write down questions your asked in interviews and share with the discord
- MAKE SURE YOU KNOW WHAT YOU KNOW REALLY WELL


Zeinab
- Don't keep adding things when your talking, have your talking points organized and concise, answering the question at hand


