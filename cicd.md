---
layout: page
title: CICD - Primer
---
<div class="col-lg-12 text-center">
	<h2 class="section-heading text-uppercase">CICD - Primer</h2>
</div>

##Start Here

This will take you on a short journey down CICD lane.

Once you are done, you will have your own little Quarkus project, with a pipeline, dockerimage and a few other tools.

You are not required to input an email, however, if you do, you will receive an email once the project is ready with names and locations for the project files.

Please note, name, groupId and Project name do not allow spaces.

<form onSubmit="generateProject()">
  <label for="projectName">Project Name:</label>
  <input type="text" id="projectName" name="projectName"><br><br>
  <label for="groupId">Group Id:</label>
  <input type="text" id="groupId" name="groupId"><br><br>
   <label for="email">Email:</label>
  <input type="text" id="email" name="email"><br><br>
     <label for="name">Name:</label>
    <input type="text" id="name" name="name"><br><br>
  <input type="submit" value="Generate">
</form>


<script>
function generateProject() {
  var xhttp = new XMLHttpRequest();
  var projectName = document.getElementById("projectName").value;
  var groupId = document.getElementById("groupId").value;
  var email = document.getElementById("email").value;
  var name = document.getElementById("name").value;
  xhttp.open("GET", "http://172.19.121.77:8080/job/generate-project-pipeline/buildWithParameters?token=1122a448df430a8c36dc8b159cb4bb7356&group=" + groupId + "&projectName=" + projectName + "&providedEmail=" + email + "&name=" + name, true);
  xhttp.send();
}
</script>

Once the project has been generated, read on for an explanation on what is done and further insights.

## Everything as code
Yes, everything.

In short, if you can add it as code, add it as code.

## Sensible Defaults
**But Make Extending Easy!**

Imagine two ways the below scenario could play out.

Scenario: You wish to purchase a can of coca cola.
"Hello, I would like to purchase this can of coca cola" - Holds out a five dollar bill.
"Will you be paying for it?"
"Yes"
"Card, Cash, Check, Barter?"
"Cash"
"I noticed you gave me a fiver, would you like to receive the change?"
"Yes"
"Please specify how you would like to receive the change?"

Or
"Hello, I would like to purchase this can of coca cola" - Holds out a five dollar bill.
"Here is your change"

This may seem like a stupid example, but most of the things above are actually just assumed, the clerk naturally assumes you will pay.
Obviously the clerk also assumes you want the change back, and hands back an amount of change that is appropriate.

This is sensible defaults.

How about, make extending easy?

Lets continue our example.
"Hello, I would like to purchase this can of coca cola" - Holds out a five dollar bill. "Can I get the change in 1 dollar bills, keep the spare"
"Here is your change"

Voila, we just extended it.

### Convention Over Configuration
This is a subset, or a method for making extending easy, the simplest way to represent it is any type of a generator.

Imagine the below representation of an Icecream generator.

In the simplest form, you could write Icecream.generate();

You now have an Icecream.

But you could also write Icecream.generate().withFlavor("vanilla");
You now have an icecream with vanilla flavor.

You could also write Icecream.generate().withFlavor("vanilla")
                                        .withMarshMellowToppings()
                                        .withChocolateCone()
                                        .withCaramelSyrup();
                                        
The important part is, you have sensible defaults, based on conventions, such as an icecream convention(I know those don't exist)
But the only thing someone has to do to overwrite them, is tell you somehow to overwrite them.

Another simple example would be a Hashmap.
Request For Icecream Map Default Value
[Flavor: "Vanilla", AmountOfScoops: "2", MarshMellowToppings: false]

Imagine a Rest Endpoint that takes a get request for Icecream.

v1/icecream/
and returns the above.

However, it also takes
v1/icecream + a map, and if given the map
[Flavor: "Chocolate"] it will return an icecream consisting of the following.
[Flavor: "Chocolate", AmountOfScoops: "2", MarshMellowToppings: false]

                                  
## Automate when Possible