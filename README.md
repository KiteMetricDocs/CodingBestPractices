# THIS DOCUMENT IS UNDER CONSTRUCTION

The best practices which are not be able to checked by automatic tools.

Scope: general programming and javascript.

# Naming
Choose the names carefully. If you can't name well, you probably can't manage your code.
* Choose descriptive name. Examples:

*Bad*: var d; // elapsed time in days
*Good*: var elapsedTimeInDays;

TODO add more examples
* Keep the name short if possible. However, don’t be afraid of long name if it is necessary to describe object. Normally, the larger scope the name is the longer length it is.
* Use Pronounceable and correct English names
* Use Searchable Names. Single-letter names and numeric constants have a particular problem in that they are not easy to locate across a body of text.
* Methods should have verb or verb phrase
* Classes and objects should have noun or noun phrase
* Boolean variable name should have `is` prefix. Sometimes `can`, `should`, or `has` can be used when appropriate. E.g. isVisible, shouldUpdate, canAbort, hasEntity.
* Keep the name up to date with the implementation
* ....

# Duplication
* Avoid copy and paste code
<details>

<summary>Examples</summary>
  
<p>
  
### BAD
``` javascript
      const initialOrganizationLinkOptions = props.organizationLinks.map((obj) => {
          return { value: `${obj.id}accessLevel${AccessLevel.READ_DOWNLOAD.value}`,
                  label: `${obj.name} ${AccessLevel.READ_DOWNLOAD.name}` };
      });
      
      //.... 
      // And in another function:
      const organizationLinkOptions = selectedOrganizations.map((obj) => {
          return { value: `${obj.id}accessLevel${AccessLevel.READ_DOWNLOAD.value}`,
                  label: `${obj.name} ${AccessLevel.READ_DOWNLOAD.name}` };
      });
```
### GOOD
Create a function to convert organization link data into select option, then reuse at 2 places

``` javascript
      const initialOrganizationLinkOptions = convertToSelectOptions(props.organizationLinks);
      
      //.... 
      // And in another function:
      const organizationLinkOptions = convertToSelectOptions(selectedOrganizations);
```

</p>

<p>
  
### BAD
The date time formatting appears several places due to copy & paste
```javascript
 const createdDateTimeText = moment(data.createdAt).format('YYYY-MM-DD HH:mm');
 ...
 
 const loginDateTimeText = moment(data.loginAt).format('YYYY-MM-DD HH:mm');
 
```
### GOOD
Create a unified date time format function for whole application. For example: formatDateTime, formatDate, formatTime,...

</p>

</details>

* Avoid different code but the same logics
* Avoid different variables keep the same information (to try keep single source of truth).
# Error handling
* NEVER catch error and keep silent.
* Each exception that you throw should provide enough context to determine the source and location of an error
* Create informative error messages and pass them along with your exceptions. Mention the operation that failed and the type of failure.

TODO give examples

# Performance
## N+1 problems
## Be careful with premature optimization
...
# Comments
* You should first strive to make your code as simple as possible to understand. Then at the point where the code cannot be made easier to understand should you begin to add comments. For example:
* Explain “why” you must write the code in a certain way, what the rationale for choosing this or that method is, etc.
* Explain how the code works when your write complex algorithm.
* Keep the comments up to date.
* Avoid redundant comments. A comment is redundant if it describes something that adequately describes itself. For example:

i++; // increment i
* Remove Commented-Out Code. We don’t need to keep the old code by commenting-out, the source control does this. And most of the time, commented-out code is useless.
* At the top of the definition of a function, a short description should be provided, explaining what the function is aiming to do, what are the parameters. Especially, in most of scripting languages, it is important to indidate the type of the input paramenters.   
# Function design
* Keep the function small and does one thing well
* The number of arguments should smaller than 3.
* A function should have NO side effects
# Complexity
## Keep technical code away from business code
# Others
### Avoid magic number
Magic number is hard to understand and hard to update. Define them as meaning full constant.

<details><summary>Example</summary>
<p>

#### BAD
```javascript
if (activeTab === 1) {
 // do something
} else if (activeTab === 3) {
 // do something.
}
```
#### GOOD
```javascript
const GENERAL_TAB_INDEX = 1;
const MEMBERS_TAB_INDEX = 3;

if (activeTabIndex === GENERAL_TAB_INDEX) {
 // do something,
} else if (activeTabIndex === MEMBERS_TAB_INDEX) {
 // do something.
}
```

</p>

<p>

#### BAD

```javascript
const numberOfFrames = video.length * 48;

//  at another place.

const video.length = numberOfFrames / 48;

```

#### GOOD

```javascript
const NUMBER_OF_FRAMES_PER_SECOND = 48;

const numberOfFrames = video.length * NUMBER_OF_FRAMES_PER_SECOND;

//  at another place.

const video.length = numberOfFrames / NUMBER_OF_FRAMES_PER_SECOND;

```

</p>

</details>
### Commit messages
