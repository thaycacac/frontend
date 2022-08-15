|var|let|const|
|---|---|---|
|The scope of a var variable is functional scope.|The scope of a let variable is block scope.|The scope of a const variable is block scope.|
|It can be updated and re-declared into the scope.|It can be updated but cannot be re-declared into the scope.|	It cannot be updated or re-declared into the scope.|
|It can be declared without initialization.|It can be declared without initialization.|It cannot be declared without initialization.|
|It can be accessed without initialization as its default value is “undefined”.|It cannot be accessed without initialization, as it returns an error.|It cannot be accessed without initialization, as it cannot be declared without initialization.|
