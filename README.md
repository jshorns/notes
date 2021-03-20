# Group project - Notes

A single page front end vanilla javascript app for note taking. This project was developed as a group up to the point of fulfilling all the user stories and project requirements, and then forked individually to develop our own styling and further functionality. This is my version of the project after that individual further development.

## App functionality

### How to use

* The app loads in the view for adding a note and viewing the note list as a default. When notes are added, an abbreviated version is added to the notes list which appears below the text box. Each abbreviation acts as a link to the note view, where the full text of the note can be seen.
* You can include emojis in notes by using shortcodes. These are converted into emojis via the [Makers emojify API](https://makers-emojify.herokuapp.com/).
* Notes are stored to local storage. The full list can be cleared at any time through the 'clear notes' button, and individual notes can be deleted from their individual note views.
* The app offers different styles, each based on a different comic. Pressing the 'New Comic' button will randomly pick a new style. At present there are 3 styles available, but more could easily added.

### Screenshots

## This is fine

![Note list view.](/images/screenshots/thisisfinelist.png "Note list view.")
![Note view.](/images/screenshots/thisisfinenote.png "Note view.")


## Oh no

![Note list view.](/images/screenshots/ohnolist.png "Note list view.")
![Note view.](/images/screenshots/ohnonote.png "Note view.")


## MF Breadcrumbs

![Note list view.](/images/screenshots/mfbreadcrumbslist.png "Note list view.")
![Note view.](/images/screenshots/mfbreadcrumbsnote.png "Note view.")


### Ideas for further functionality

* Adding further styles, as per the above. This would require some changes for scaleability. Currently each style has its own stylesheet, but this could be refactored into assigning the values that would need changing (background image and colours) to variables, which would be assigned as css properties on changing styles (in the same manner that changing the link to the stylesheet itself currently is).
* Editing notes, tagging notes, commenting on notes.
* Confirmation messages when notes are added, confirmation alerts when deleting or clearing notes.


## Project process

### Project challenges

* To create a web app that only uses a single page.
* To do so without using any external libraries, such as jQuery or Jasmine.
* To develop the app in a TDD way.

### User stories

```
As a programmer
I can see a list of my notes, where each note is abbreviated to the first 20 characters
So I can find the one I want
```
```
As a programmer
I can create a new note
So I can record something I need to remember
```
```
As a programmer
I can see the full text of an individual note on its own page
So I can see all the information in the note
```
```
As a programmer
I can use shortcodes like `:fire:` that get converted into emojis like 🔥
So I can record notes with fun little pictures
```

## Tests

* There are unit tests and some feature tests, which run based on an unstyled version of the app. Both are written using the testing framework which can be found in the javascript/spec folder.
* To run the tests, open the respective html file from the javascript folder in your browser. This loads and runs both the src and spec files.
* Open the console to view pass and fail messages for the tests.
* Because of the extra loading time of the API, the feature tests are grouped within a setTimeout, so these run a little slower.

## Process

* We began by writing javascript classes we felt would be needed to meet the needs of the program. This included a notebook class, which we ended up not needing as the same could be achieved by storing the notes to a list within the array.
* We also diagrammed our initial thoughts on how the interface would work.
* We then wrote unit tests for these classes - these were very basic to begin with, simply if/else conditionals printing to the console.
* We then worked on the interface individually, to meet the first 3 user stores, so everyone could practice with vanilla javascript, and came back to pull our versions together.
* We then worked in pairs on developing the testing framework and integrating the API.
* We worked together to finish off the testing, to deploy the app, and to integrate storing notes to local storage, both of which were additional goals to the user stories.
* Having fully met the brief, we then worked individually on implementing styling and further functionality.

## Diagrams

![Sequence diagram for creating a note.](/images/diagrams/create_note_seq_diagram.png "Sequence diagram.")

#### diagrams.codes code for this diagram:


```
alias u="User"
alias i="Interface/browser"
alias nb="Notebook"
alias n="Note"

u->i:"Navigate to page"
i->nb:"create new instance of notebook"
nb-->i:"return new instance of notebook"
i-->u:"Render index.html"
u->i:"enter note details + click submit"
i->n:"create new note instance"
n-->i:"return new note instance"
i->nb:"store new note in notebook"
nb->nb:"add note to array/hash"
nb->nb:"function to generate 20char descriptions"
nb-->i:"return 20char descriptions"
i->i:"update html file with descriptions"
i-->u:"render index.html"
```
