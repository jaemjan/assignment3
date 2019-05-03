# assignment3
Software Architecture Design
Asian Institute of Technology

Assignment 3: Microservice + Serverless Architecture
________________________________________

-	Title: microservice with spring boot
-	Member names: Jaemjan  st119831
-	Describe the 3rd party microservice you use and why you use it (2pts)
I use Spring Boot to develop microservice: spring boot is easy to create stand-alone, production-grade, it easy dependency management, have auto configuration and embedded servlet container support.
I use this application because this program no need for server, it’s easy to map with http.
-	Describe your own microservice and why you made it (2pts)
I do the 3 microservices for movie system: 1) Movie Info service  2) Rating Date service and 3) Movie Catalog service. The process to create that show the detail below:

1) From Spring Boots I should create 3 Spring Boot projects.
    - go to https://start.spring.io/
    - create group, artifact, package Java, Java version (this project use Java version 11)  and select Web dependencies.
2) Build input form service by create the controller.ja,main_page.html,form.html and Contact.java
-	Describe your usage of serverless technology (1pt)
Serverless technology is very easy to user because it can access the system anywhere anytime. It’s easy to create application.
-	Describe your implementation briefly (best with sample code snippets) (1pt)
I create the form input by using classes , first create class for controller, second create class for service, after create this classes that mean we connect frontend and backend. And last create application for repository the data. For all implement the microservice by using spring boot we start with create @component, @service, @Controller and @Repository.

Sample for the code below:
helloController.java

package com.example.demo;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.ModelAttribute;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.ResponseBody;

import com.example.demo.model.Contact;

@Controller
@RequestMapping(value="/")
public class helloController {
	@RequestMapping (method=RequestMethod.GET)
	public String index()
	{
		return "main_page";
	}
	@RequestMapping(value="/form")
	public String form()
	{
		return "form"; 
	}
	@RequestMapping(value= "/save")
	@ResponseBody
	public String save(@ModelAttribute Contact c)
	{
		return "Hello :"+c.getfEmail()+"\n"+c.getfName();
	}
}


main_page.html
<!doctype html>
<html lang="en">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">

    <title>Hello, world!</title>
  </head>
  <body>
    <h1>Hello, world!</h1>

    <!-- Optional JavaScript -->
    <!-- jQuery first, then Popper.js, then Bootstrap JS -->
    <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>
  </body>
</html>

form.html

<!doctype html>
<html lang="en">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">

    <title>Form</title>
  </head>
  <body>
    <h1>form</h1>
<form method="POST" action="/save">
  <div class="form-group">
    <label for="exampleInputEmail1">Contact name</label>
    <input type="text" class="form-control" id="fName" name="fName" aria-describedby="emailHelp" placeholder="Enter email">
    <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
  </div>
  
  <button type="submit" class="btn btn-primary">Submit</button>
</form>
    <!-- Optional JavaScript -->
    <!-- jQuery first, then Popper.js, then Bootstrap JS -->
    <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>
  </body>
</html>

contact.java
package com.example.demo.model;

public class Contact {
	private String fEmail;
	private String fName;

	public String getfEmail() {
		return fEmail;
	}

	public void setfEmail(String fEmail) {
		this.fEmail = fEmail;
	}

	public String getfName() {
		return fName;
	}

	public void setfName(String fName) {
		this.fName = fName;
	}
}



-	A diagrams/graphs explaining the architecture of the whole app (1pt)

1) Customer Info service
    Input: CustomerID
    Output : Customer Details

























Spring Boot Architecture:

 
-	Discuss the pros/cons of microservice and serverless technology in your own words (3pts)



Microservice technology


PROS	CONS
Specific for small problem	Cascading failure.
Can build and deploy by itself (stand alone)	Often for changing to develop.
Can Runs in its own process.	Data Consistency, Data Integrity
Can Integrates via well-known interfaces	Fault Tolerance
Have own data storage	Diagnostics
Help for complexity programing	Cascading failure
Microservices rely on each other, developer can easy to communicate with each other. Helps to give emphasizes on a specific feature and business needs.	
Dynamic scaling.	

Serverless technology

PROS	CONS
No need for buying the Server.	Vendor Lock-in - difficult to move if completed Because it will bind to that cloud provider at all (except in the future there will be an easy way to move). For example, Amazon's use will change to Google Cloud.
Can access anytime and anywhere.	Engineering Difficulty - System planning requires what to connect with. Because everything is separate, it's a small function. If there is no good planning, it can be easily done. If there is anything broken, check it hard because the link system is a lot.
don’t need to manage, or maintenance anymore.	
Easy to create application for developer.	
Faster time to market.	
Developer don’t have to worry about administering infrastructure:run time environments, security updates, OS patches, scaling, capacity,etc.	
Developer focus on writing software.	
Simple performance.	


