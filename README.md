# hw06 Server-Side APIs: Weather Dashboard
5-day weather dashboard using fetch and server-side apis. Michael Sheliga 10.26.26

## Links
Deployed HTML Link: "https://urimjs.github.io/hw06fetchURLVB/"  
GitHub Repo Link: "https://github.com/uriMJS/hw06fetchURLVB.git"   
Screenshot Question Link: ![Screenshot of program with with saved cities](./assets/Screenshot06Cities.png)   
Screenshot HiScore Link: ![Screenshot of program with with cities cleared](./assets/Screenshot06Clear.png)
	
## Significant Programming Features   
This project was long, with a few tricky bugs.    
**Javascript** Lots of DOM manipulation, much of it common.  
   - document.createElement, Element.appendChild, Button.addEventListener   
   - Element.remove() used to reset main section  
   - "Global" values kept in the DOM (question-index, time-left, Message, interval-id).  
   - intervalId = setInterval(callback method, time)
      - No inner functions since intervalID kept in DOM  
	  - clearInterval(intervalId) in checkAnswer need not be inisde setInterval  
   - Used two js files. script.js and hiScores.js. 	  
   - Used split(index, length, insertItem) for ordered HiScore list.    
   - **Issue** Buttons displayed in-line, even when inside block or flex-direction column.  
      - Solution: Use a div to surround each button.  
   - Button Click Handler - 4 Methods - onclicks and addEventListener 
      - Documentation at www.xjavascript.com/blog/how-to-set-onclick-with-javascript/   
      - button onclick="handler(event)" tag and button.setAttribute("onclick", "checkAnswer(event)")
         - Note onclick, not onClick  
		 - Both handlers gets quotes, parenthesis and event  
	  - button.onclick = checkAnswer and button.addEventListener("click", handler)  
	     - No handler quotes, parenthesis nor event  
         - addEventListener is only method using "click" instead of "onclick"	
   - **Issue** Form submit button returned to main screen. (Replicated at end of project for testing.)  
      - Solution: Use event.preventDefault  
	  - Note that this problem occurs if handler only has alerts, but not if screen is re-rendered.  
 
**CSS**  
   - Multiple button classes (normal and disabled) with different background-colors.  
      - Use to gray out disabled answer. 
   - Class later in CSS controls the color. class="class1 class2" order does not matter.  
 
**To Learn From**  
   - LocalStorage  
      - Used LocalStorage to Keep HiScores  
         - .removeItem, .setItem, .getItem	 
      - Must Store Strings in LocalStorage => JSON.stringify  
      - Need Array out of LocalStorage => JSON.parse  
   - Disabled button with button.setAttribute("disabled", "disabled")  
      - Second values does NOT matter here. 
	  - Use button.removeAttribute("disabled") to enable.
	  - Inconsistent documentation on button.disabled = false;
	  
**Tools** (Aint nothing more important than your tools)  
   - Webpage Debugger. CNTL-SHIFT-J  
      - Set breakpoints and inspected variables.  
      - LocalStorage. Found and deletable under Attributes tab.  
	  - CSS values. Can find striken DOM properties, such as margin, but not why they were striken.
	  
## Notes  
No starter code (index.html, style.css, script.js and a .png file) for this project.   
**All code, including CSS written from scratch.**    
The programming was pretty straight-forward, but long. Lots of adding elements to DOM.   
Screenshot Link: This image seems to only show up in github.  
For screenshot ![Text] is just explanatory text.   
Deployment: To create githubio deployment    
   - Go to the repo (github.com/uriMJS/uriHW04jsTimedQuizVB).   
   - Click on the **Settings** button.  2nd Row of Icons from top, far right.  
   - Click on the Pages button.  Left menu list, about 60% down.  
   - Github Pages Screen Should Appear  
      - Click on Source -> Deploy From a Branch (near screen center)  
	  - Click on Branch -> main: root (just below Source)  

## Acceptance Criteria  
	Click the start button: timer starts and I am presented with a question  
	answer a question, presented with another question
	answer a question incorrectly, time (15) is subtracted from the clock
	all questions are answered or the timer reaches 0, game is over
	game is over, can save my initials and score.  
	Note Tweaks: Total time of 10, wrong answer => 5 second penalty and disabled button. 



## Your Task

Third-party APIs allow developers to access their data and functionality by making requests with specific parameters to a URL. Developers are often tasked with retrieving data from another application's API and using it in the context of their own. Your challenge is to build a weather dashboard that will run in the browser and feature dynamically updated HTML and CSS.

Use the [5 Day Weather Forecast](https://openweathermap.org/forecast5) to retrieve weather data for cities. The base URL should look like the following: `https://api.openweathermap.org/data/2.5/forecast?lat={lat}&lon={lon}&appid={API key}`. After registering for a new API key, you may need to wait up to 2 hours for that API key to activate.

**Hint**: Using the 5 Day Weather Forecast API, you'll notice that you will need to pass in coordinates instead of just a city name. Using the OpenWeatherMap APIs, how could we retrieve geographical coordinates given a city name?

You will use `localStorage` to store any persistent data. For more information on how to work with the OpenWeather API, refer to the [Full-Stack Blog on how to use API keys](https://coding-boot-camp.github.io/full-stack/apis/how-to-use-api-keys).

## User Story

```
AS A traveler
I WANT to see the weather outlook for multiple cities
SO THAT I can plan a trip accordingly
```

## Acceptance Criteria

```
GIVEN a weather dashboard with form inputs
WHEN I search for a city
THEN I am presented with current and future conditions for that city and that city is added to the search history
WHEN I view current weather conditions for that city
THEN I am presented with the city name, the date, an icon representation of weather conditions, the temperature, the humidity, and the wind speed
WHEN I view future weather conditions for that city
THEN I am presented with a 5-day forecast that displays the date, an icon representation of weather conditions, the temperature, the wind speed, and the humidity
WHEN I click on a city in the search history
THEN I am again presented with current and future conditions for that city
```

## Mock-Up

The following image shows the web application's appearance and functionality:

![The weather app includes a search option, a list of cities, and a five-day forecast and current weather conditions for Atlanta.](./Assets/06-server-side-apis-homework-demo.png)

## Grading Requirements

> **Note**: If a Challenge assignment submission is marked as “0”, it is considered incomplete and will not count towards your graduation requirements. Examples of incomplete submissions include the following:
>
> * A repository that has no code
>
> * A repository that includes a unique name but nothing else
>
> * A repository that includes only a README file but nothing else
>
> * A repository that only includes starter code

This Challenge is graded based on the following criteria: 

### Technical Acceptance Criteria: 40%

* Satisfies all of the above acceptance criteria plus the following:

    * Uses the OpenWeather API to retrieve weather data.

    * Uses `localStorage` to store persistent data.

### Deployment: 32%

* Application deployed at live URL.

* Application loads with no errors.

* Application GitHub URL submitted.

* GitHub repository that contains application code.

### Application Quality: 15%

* Application user experience is intuitive and easy to navigate.

* Application user interface style is clean and polished.

* Application resembles the mock-up functionality provided in the Challenge instructions.

### Repository Quality: 13%

* Repository has a unique name.

* Repository follows best practices for file structure and naming conventions.

* Repository follows best practices for class/id naming conventions, indentation, quality comments, etc.

* Repository contains multiple descriptive commit messages.

* Repository contains quality readme file with description, screenshot, and link to deployed application.

## Review

You are required to submit BOTH of the following for review:

* The URL of the functional, deployed application.

* The URL of the GitHub repository. Give the repository a unique name and include a readme describing the project.

- - -
© 2023 edX Boot Camps LLC. Confidential and Proprietary. All Rights Reserved.
