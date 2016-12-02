# Code Analysis

See comments in `index.html` for instructions.

## Run

Open `index.html` in Google Chrome.

## Style Guide

### Git Commit Messages

- Use the present tense ("Add feature" not "Added feature")
- Use the imperative mood ("Move cursor to..." not "Moves cursor to...")
- Limit the first line to 72 characters or less
- Reference issues and pull requests liberally
- Consider starting the commit message with an applicable emoji:
    - **Improvements**
        - :art: `:art:` when improving the format/structure of the code
        - :fire: `:fire:` when removing code or files
        - :tada: `:tada:` when adding a feature
        - :goat: `:goat:` when improving performance
    - **Misc**
        - :memo: `:memo:` when writing docs
    - **Dependencies**
        - :arrow_up: `:arrow_up:` when upgrading dependencies
        - :arrow_down: `:arrow_down:` when downgrading dependencies

### React Styles

- Always favor stateless components


### Pers Comments

Hello! This was a fun exercise. I've made a few tweaks to this codebase, and I'll outline my decision making below.

1 - I created the getName function (line 134) to remove the duplication of the two previous functions getLastName and getFirstName. These are virtually identical functions, whose only difference is the index of the array, stemming from the match regular expression, which they return. Instead of these two functions, I created a single function which accepts an object as an argument, whose properties are "name", and "key."

The index object within this function can be referred to with the key parameter, and identify the array index of the matched regular expression, and return the desired name.

Because of this change, I also had to update lines 240 and 241 so as to executed with the property argument properties.

2 - I made a small change to the filterByName function (line 165) by calling .toLowerCase on both names. This would accommodate for the users whose input may not match the capitalization style of the employee's name property.

Also, I included the .includes function, instead of === since JS can compare two strings and identify if one string contains the letters (in their specific order) within the other. Since the Search input has an onChange function, which triggers the _onSearch() function, this will update the state of our app immediately._

3 - For the sortObjListByProp function (line 188), I first built a series of validations to compare the sorting of our objList. I made the assumption that if the first, last, and a random index of these two lists (the result list and objList list) shared identical names, we can presume they are in identical order, and should therefore, be reversed.

Initially, my logic only executed correctly on the first click, ordering the employees by their full name in descending order.

After further review, I identified the issue. Instead of providing the state's personList array, which is static throughout the whole app, I provided the visiblePersonList as the objList parameter for the sortByLast and sortByFirst functions.

Not only does this now provide a "toggle" like experience, but still be utilized when users search for an employee by a partial spelling.

I also changes its paramter input to accept a args object with two properties: prop, and type.

4 - Lastly, I refactored the consts sortByFirstName and sortByLastName (lines 215 and 218) to send its args' two properties.
