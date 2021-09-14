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

Deleteing:

The branch still exists after merging so we should clean it up if no longer needed. Keep in mind that the branches exist bot on our machine in git AND on github, so we need to delete both.

Make sure you ARE NOT in the branch your going to delete.

Delete github branch
git push origin :adding-content

Delete local git branch
git branch -d adding-content

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

null	: falsy
undefined : falsy
any string :	truthy
an empty string :	falsy
the number 0 :	falsy
any number higher or lower than 0 :	truthy


## Functions


- Functions are FIRST CLASS CITIZENS which means they are just values


Function Declartion:

- Hoisted

```js
function helloWorld() {
  console.log('Hello World')
}
```

Function Expression:

- The definition of a function stored in a variable
- An anonymous function stored in the variable
- Not hoisted

```js
const helloWorld = function() {
  console.log('Hello World')
}
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
    lrg: 10
  }
}

clothing.socks
// 34


clothing["shoes"]
//  2


const userChoice = prompt('What item do you want to know about?');
//  The user picks shoes, so now we have the string "shoes"


clothing[userChoice]
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
  pants: 3
}

for (let item in clothing) {
  console.log(`I have ${clothing[item]} ${item}`);
}
```



