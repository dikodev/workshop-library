## Build A Static Website - Community Site
This is a sample static website that can be used to build a static website using Azure Static Web Apps. This site is built using [Hugo](https://gohugo.io/) and is based on the [Hugo Learn Theme](https://learn.netlify.app/en/).

## Prerequisites
1. VS Code 
2. An Azure Subscription

## What students will learn
Smart Shopping Planner is a React application built using JavaScript, that stores data in an Azure SQL database. In this blog, I want to show you how incredibly easy it was to provide REST endpoints (you can work with GraphQL too) to connect the app to the database.

## Lab Milestones

1. **Create an index.html file in VSCode** 
    - Add the following code to the index.html file
    ```
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Static Web Apps Community Site</title>
    </head>
    <body>
        <h1>Static Web Apps Community Site</h1>
    </body>
    </html>
    ```
    - Save the file

2. **Update the head tag with the following code**
    ```
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <title>Contoso Community</title>
        <meta name="description" content="">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <link rel="stylesheet" href="style.css">
        <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">

        <script src="main.js" type="javascript" ></script>
    </head>
    ```
3. **Update the body with following code** 
    ```
    <body>
    <!--Navbar-->
    <nav class="navbar navbar-default navbar-fixed-top">
        <div class="container">
            <div class="navbar-header">
                <a href="#" class="navbar-brand">Home</a>
            </div>
            <div class="collapse navbar-collapse">
                <ul class="nav navbar-nav navbar-right">
                    <li><a href="#">About</a></li>
                    <li><a href="#">Contact Us</a></li>
                    <li><a href="#">Sign Up</a></li>
                    <li><a href="#">Login</a></li>
                </ul>
            </div>
        </div>
    
    </nav>

    <!--Heading text about Contoso Community-->
    <div class="jumbotron">
        <div class="container">
            <h1>Contoso Community</h1>
            <p>Welcome to Contoso Community, a vibrant hub for both professional and low-code developers! Whether you're an experienced programmer looking to sharpen your skills or someone who wants to dive into the world of coding with minimal effort, our community is the perfect place for you. 
            </p>
            <p><a href="#" class="btn btn-primary btn-lg" onclick="document.getElementById('id01').style.display='block'">Learn more</a></p>
        </div>
       
    </div>
    <!--About Contoso Community-->
    <div class="container">
        <div class="row">
                <div class="col-sm-12">
                <h2>About Contoso Community</h2>
                <p style="font-size: large;">Contoso Community is a vibrant hub for both professional and low-code developers! Whether you're an experienced programmer looking to sharpen your skills or someone who wants to dive into the world of coding with minimal effort, our community is the perfect place for you. 
                    Join a diverse and supportive network of like-minded individuals who share a passion for technology and innovation. 
                </p>
                <p style="font-size: large;">
                    Connect with experts, collaborate on projects, and exchange ideas through our forums, workshops, and events. With a focus on both traditional programming and low-code development, Contoso Community offers a unique opportunity to explore different approaches and expand your knowledge.
                </p>
                <br>
                <button class="btn btn-default btn-lg">Sign Up</button>
            </div>
        </div>
       
    </div>
    <!--Community YouTube Videos-->
    <div class="container">
        <h2>Community & Videos</h2>
        <div class="row">
            <div class="col-sm-4">
                <h3>Building NLP Products with OpenAI</h3>
                <iframe width="380" height="350" src="https://www.youtube.com/embed/_KGuW7y3I6s" title="Building NLP Products with OpenAI" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
            </div>
            <div class="col-sm-4">
                <h3>Building AI Products with Hugging Face</h3>
                <iframe width="380" height="350" src="https://www.youtube.com/embed/T6GPytSmUQM" title="Building AI Products with Hugging Face" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
            </div>
            <div class="col-sm-4">
                <h3>End to End Power BI Project with DAX Suggestion</h3>
                <iframe width="380" height="350" src="https://www.youtube.com/embed/4mbXIbZAyM4" title="End to End Power BI Project with DAX Suggestion" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
            </div>
        </div>
    </div>
    <!--Community Events--> 
    <div class="container">
        <h2>Community Calls & Events</h2>
        <div class="row">
            <div class="col-sm-6">
                <h3>Get Started With GitHub</h3>
                <!--Add an Event image for Github-->
                <img src="https://marcas-logos.net/wp-content/uploads/2020/03/GITHUB-LOGO-1024x576.png" alt="Lights" style="width:100%; height: 40%;">
                <br>
                <p style="font-size: large;">This exciting event designed to help you kickstart your journey into the world of version control and collaboration.  </p>
                <!--Add a date and time-->
                <p style="font-size: large;">12/10/2023</p>
                <!--Add a Sign up button-->
                <button class="btn btn-default btn-lg" onclick="document.getElementById('id01').style.display='block'">Sign Up</button>
            </div>
            <div class="col-sm-6">
                <h3>Build your First App Using PowerApps Canvas Apps</h3>
                <!--Add an Event image for Github-->
                <img src="https://365digitalconsulting.com/wp-content/uploads/2021/06/Powerapps-V2-1024x524.jpg" alt="Lights" style="width:100%; height: 40%;">
                <!--Add an Event description-->
                <p style="font-size: large;">Join us as we dive into the world of PowerApps and guide you through the process of creating dynamic and user-friendly apps. </p> 
                    
                <p style="font-size: large;">12/09/2023</p>
                <!--Add a Sign up button-->
                <button class="btn btn-default btn-lg" onclick="document.getElementById('id01').style.display='block'">Sign Up</button> 
            </div>
            <div class="col-sm-6">
                <h3>Get Started with AI Builder in Power Platform </h3>
                <!--Add an Event image-->
                <img src="https://www.velosio.com/wp-content/uploads/2020/07/AI-Builder-4-1536x864.jpg" alt="Lights" style="width:100%; height: 40%;">
                <p style="font-size: large;"> Learn how to create AI models without writing code, automate processes, and gain insights from your data using AI. Don't miss this chance to harness the power of AI and transform your business.</p>
                <p style="font-size: large;">12/08/2023</p>
                <!--Add a Sign up button-->
                <button class="btn btn-default btn-lg" onclick="document.getElementById('id01').style.display='block'" >Sign Up</button>
            </div>
            <div class="col-sm-6">
                <h3>Build a Custom Connector from a Web API</h3>
                <!--Add an Event image-->
                <img src="https://vblogs.in/wp-content/uploads/2021/03/image-86.png" alt="Lights" style="width:100%; height: 40%;">
                <p style="font-size: large;">Join us for an immersive and hands-on workshop, this is designed to empower developers of all levels with the knowledge and skills to create powerful custom connectors for their applications.</p>
                <p style="font-size: large;">12/07/2023</p>
                <!--Add a Sign up button-->
                <button class="btn btn-default btn-lg" onclick="document.getElementById('id01').style.display='block'">Sign Up</button>

            </div>
        </div>
    </div>
  
    <!--Footer-->
    <footer class="text-center">
        <a href="#myPage" title="To Top">
            <span class="glyphicon glyphicon-chevron-up"></span>
        </a>
        <p>Contoso Community</p>
    </footer>
    </body>
    ```

3. **Add the following code to the body add a Modal with a Form for user input**
    ```
      <!--Add a Modal (hidden by default) with styling-->
    <div id="id01" class="modal">
        <form id="CommunityForm" class="modal-content animate" action="/action_page.php">
            
            <div class="imgcontainer">
                <span onclick="document.getElementById('id01').style.display='none'" class="close" title="Close Modal">&times;</span>
                <!--<img src="img_avatar2.png" alt="Avatar" class="avatar">-->
            </div>
            <div class="formTitle">
                <h3><img style="height: 50px; width: 50px;" src="https://th.bing.com/th/id/OIP.RX6ZM7w3p6fyGTuw-UjsNAHaHa?pid=ImgDet&rs=1"/> Join the Community</h3>
            </div>
            
            <!--Add a div with labes and texboxes for Name, Surname and Email-->
            <div class="container" style="height: 500px;">
                <label class="textInput"><b>Name</b></label>
                <input type="text" placeholder="Enter Name" name="Fullname" id="name" required>
    
                <label class="textInput"><b>Surname</b></label>
                <input type="text" placeholder="Enter Surname" name="surname" id="surname" required>
    
                <label class="textInput"><b>Email</b></label>
                <input type="text" placeholder="Enter Email" name="email" id="email" required>
    
                <label class="textInput"  for="linkedin"><b>LinkedIn</b></label>
                <input type="text" placeholder="Enter your LinkedIn Url" name="linkedin" id="linkedin">
                <input type="submit"  class="Mybutton" value="Submit">
                <p class="terms">By clicking submit you agree to our <a href="#">Terms & Privacy</a> and receiving community updates!</p>
            </div>

            
        </form>
    </div>
    ```

4. **Add the following code to the body to add a script to handle the form submission and modal**
    ```
    <script type="text/javascript">
    //Write a JSON script to make an HHTP POST request from CommunityForm form.
    CommunityForm.onsubmit = async (e) => {
               e.preventDefault();
               var form = document.getElementById("CommunityForm");
               var data = {
                     name: form.name.value,
                     email: form.email.value,
                     linkedin: form.linkedin.value,
                     terms: "Yes"
               }
               let response = await fetch('[YOUR_FLOW_API_KEY_HERE]', {
                   method: 'POST',
                     headers: {
                          'Content-Type': 'application/json;charset=utf-8'
                     },
                   body: JSON.stringify(data)
               });
               let result = await response.json();
               alert(result.message);
           }
    </script>
    ```

5. **Add the following code to the body to add a script to handle site scroll**
    ```
    $(document).ready(function(){
        // Add smooth scrolling to all links in navbar + footer link
        $(".navbar a, footer a[href='#myPage']").on('click', function(event) {
    
        // Prevent default anchor click behavior
        event.preventDefault();
    
        // Store hash
        var hash = this.hash;
    
        // Using jQuery's animate() method to add smooth page scroll
        // The optional number (900) specifies the number of milliseconds it takes to scroll to the specified area
        $('html, body').animate({
        scrollTop: $(hash).offset().top
        }, 900, function(){
    
        // Add hash (#) to URL when done scrolling (default click behavior)
        window.location.hash = hash;
        });
        });
        
        $(window).scroll(function() {
        $(".slideanim").each(function(){
        var pos = $(this).offset().top;
    
        var winTop = $(window).scrollTop();
          if (pos < winTop + 600) {
            $(this).addClass("slide");
          }
        });
        });
    })
    ```


