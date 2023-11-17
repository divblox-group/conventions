# Code and Naming Conventions
## PHP

### Folder Naming Conventions
Folder naming needs to use the following case: **snake_case**
```php
my_folder_name/my_sub_folder_name
```
### File Naming Conventions
For file naming, we add the function/type to the file name.

| Type              | File Name                              |
|-------------------|----------------------------------------|
| background script | background_script_some_explanation.php |
| cron              | cron_some_explanation.php              |
| class             | some_new.class.php                     |

### Function Naming Code Conventions
All functions should be named using **camelCase**. The first word in a function should be a verb that describes what the function does.

```php
| Correct                  | Incorrect             |
|--------------------------|-----------------------|
| function getMyFunction() | function myFunction() |
| function hasProperty()   | function Property()   |
```
### Constants Code Conventions
All constants need to be **UPPER_SNAKE_CASE**.
The constant type should be appended to the constant name.
```php
const MY_NAME_STR = "John Doe";
define("MY_AGE_INT", 50);
define("FRUIT_ARR", ['apple', 'pear', 'grape']);
```
### Variable Naming Code Conventions
Naming variables and functions should be as descriptive as possible. **PascalCase**.
Always take into consideration that others will be working on your code in the future, 
and you want to make it as easy as possible for them to understand what you did. 
The variable type should be appended to the variable name. 

*Variables must be initialised… **ALWAYS***

##### Variable Types
| Type      | Suffix |
|-----------|--------|
| Integer   | Int    |
| Float     | Flt    |
| Double    | Dbl    |
| Boolean   | Bool   |
| Array     | Arr    |
| String    | Str    |
| Object    | Obj    |
| Character | Char   |
| Mixed     | Mixed  |
 ##### For sDev UIElements and QControls the naming convention is to add the control type as a prefix
```php
 Control Type   | Example                                                                
----------------|------------------------------------------------------------------------
 QTextBox       | $txtMyNameObj = new QTextBox();                                        
 QListBox       | $lstMyAgeObj = new QListBox();                                         
 QButton        | $btnAcceptObj = new QButton();                                         
 sUIElementBase | $sUIElementSomeHTMLObj / $SomeHTMLDisplayUIObj = new sUIElementBase();
```

### String Concatenation
A space between string concatenation operations.

```php
Correct:
$HtmlStr = '<p>' . $BenefitDisplayNameStr . ', underwritten by Someone</p>';

Incorrect:
$HtmlStr = '<p>'.$BenefitDisplayNameStr.', underwritten by Someone</p>';
```

### QQ Queries
Each QQ condition needs to be on a new line

```injectablephp
$ProductRolePlayerObjArr = ProductRolePlayer::QueryArray(QQ::OrCondition(
    QQ::In(QQN::ProductRolePlayer()->ProductObject->Id, $ActiveProductIdArr),
    QQ::In(QQN::ProductRolePlayer()->ProductBenefitObject->Id, $ProductBenefitIdArr)),
    QQ::Clause(
        QQ::Select(
            QQN::ProductRolePlayer()->Id,
            QQN::ProductRolePlayer()->Product,
        ),
        QQ::OrderBy(QQN::ProductRolePlayer()->Id)
    )
);
```
## Frontend Naming (HTML/JS/CSS)

https://www.w3schools.com/js/js_conventions.asp

### Folder/File Naming

`my_folder_name/my_sub_folder_name/script_some_explanation.js`

| HTML tag | case       | example                    |
| -------- | ---------- | -------------------------- |
| id       | camelCase  | selectedDivId              |
| class    | kebab-case | btn-primary                |
| variable | camelCase  | firstName                  |
| function | camelCase  | `toCelsius (farenheit) {}` |
| class    | PascalCase | `class Person {}`          |

> Variables are named descriptively! Without the type appended to it

| type                   | example      | description                                                         |
| ---------------------- | ------------ | ------------------------------------------------------------------- |
| number                 | productCount | Describing what is being stored                                     |
| text                   | name         |                                                                     |
| boolean                | isFinished   | Instant understanding of binary nature: try prefix with action-verb |
| object                 | person       | Describing what is being stored                                     |
| simple array           | ages         | Simple array. Always in plural                                      |
| complex array (no key) | personArray  | No key. Always singular                                             |
| complex array (key)    | personList   | Keyed. Always singular                                              |

### JS Examples

```js
// Base object, NOT pluralised when explicitly defining a singular idea/entity
let person = {
    firstName: "Gary",
    lastName: "Player",
    age: 120,
};

// Primitive array or object can be pluralised, if internals are explicitly multiple concepts/things
let persons = ["Emily", "Susan", "Gabe"];
let additionalOptions = {
    isClickable: true,
    setPreview: false,
    url: "anc.com",
};

// Array of objects (with no key)
let personArray = [
    {
        name: "Emily",
        surname: "Bester",
    },
    {
        name: "Susan",
        surname: "Venter",
    },
    {
        name: "Gabe",
        surname: "Young",
    },
];

// Object of objects (with keys)
let personList = {
    IdNumber123: {
        name: "Emily",
        surname: "Bester",
    },
    IdNumber234: {
        name: "Susan",
        surname: "Venter",
    },
    LastIdNumber: {
        name: "Gabe",
        surname: "Young",
    },
};

// Booleans - instant understanding of binary nature: try prefix with action-verb
let isComplete = false;
let hasContent = false;
let preventAction = true;
let forceReload = true;
```

### HTML Examples

```html
<input id="customInputId" class="red-border" />

<ul>
    <li data-animal-type="bird">Owl</li>
    <li data-animal-type="fish">Salmon</li>
    <li data-animal-type="spider">Tarantula</li>
</ul>
```

### CSS Examples

```css
.selected-name {
    width: 100px;
}
```

## SQL

Please use UPPERCASE for SQL operations

> Incorrect:
> select \* from Policy WHERE Id in (1,2,3);

> Correct:
> SELECT \* FROM Policy WHERE Id IN (1, 2, 3);

Storing json string in a database attribute s per the json attribute itself's naming, to avoid confusion.

-   additional_data -> {"other_first_name":"Tester"}

-   AdditionalData ->{"OtherFirstName":"Tester"}

-   Then if someone adds a column later on with the same name, it'll auto map (or gives that option in scoping).
