# Variables 

A variable is simply a container for a value to which you can give a name so you can reference the value easily. 

Think of a variable as a box. You can label the box so you can find it and so that you know what's in it, this is the variable name. The content you put inside the box is the variable value. You can change what you put inside the box as you go, which is the same as updating the variable value.

![Variable Box Diagram](/src/assets/variable_box.png)

The above diagram demonstrates a variable with a name of `userData` and a JSON value containing information about a user such as their name and age.

A variable will have an associated type such as:  
- String
- Number 
- Boolean 
- Coordinates
- Bounding Box
- Grid, 
- Image
- List 
- Date-Time 
- JSON 
- Table

All the `Activity Variable` datachips will be pink and visible in the Variables palette from the `Action Panel` (in the same section as the `Actions` and `Input/Output` tabs). `Activity Variable` datachips will always be pink whereas `Action Result` datachips are green and `Datastore Variable` datachips are blue.

So an `Activity Variable` datachip looks like this :datachip-variable[userData]{type="JSON"}.

An `Action Result` datachip looks like this :datachip-action[userData]{type="JSON"}.

A `Datastore Variable` datachip looks like this :datachip-datastore[userData]{type="JSON"}.


Variables, unlike `Action Results`, are changeable and can have their values updated throughout an `Activity`.

Variables are often created via the `Set Variable` Action but any Action Result can be used to create and set a variable (bottom of the `Action` menu). Their notation is `$$ExampleText$$`. Once they are created you can hover over their datachip to see the data.

Datachips can be renamed (they will still work in `Actions`, datachips will be updated everywhere).

To delete a variable, either click on the icon 'x' corresponding to the variable or remove the Action that created the variable.

