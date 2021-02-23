# Internship with Prosper IT Consulting

## Introduction
In the two weeks of my Internship with Prosper IT Consulting, I worked with a team to develop a full scale Code First MVC Web Application in C#. 
Working on a legacy application gave me a great learning opportunity to work out existing bugs, creating new elements, and adding completely new 
features to make the web application better as well as a more positive user experience. We delivered all needed changes in a timely fashion and met our 2 
week deadline. In my experience with the team I learned how a good software developer works in a team setting, and there were many examples of 
great leadership from the instructors. I worked on several tasks involving both front-end and back-end, and I am very proud of my code accomplishments. 
Everyone on the team had the chance to work on tasks in both front/back-end of various difficulty levels. My [final task](#Sign-In-Page-Styling) was of a high level 
of difficulty, and I am the most proud of that work. I'm confident I will use the skills I learned that are featured here for many years to come.

Below are descriptions of the tasks I worked on, along with code snippets to explore.

## Stories:
* [Sign In Page Styling](#Sign-In-Page-Styling)
* [Easy Login On Admin Navbar](#Easy-Login-On-Admin-Navbar)
* [Subscription Plan Bug Fix](#Subscription-Plan-Bug-Fix)
* [Other Skills Learned](#Other-Skills-Learned)

## Sign In Page Styling
In this task I took an existing basic and non-styled page and made it into a beautifully designed and visual appealing page. The names are added by students
as the first thing they do when they Join the live project. They add their name by creating a new p tag with their name in it. I had to style it in a way that
the sign in procedure would be simple for the new developers signing in, in other words I couldn't add tags or styles to the individual p tags. I had to find a 
way to style the tags without changing the code entered by each of the developers when signing in. I also was tasked to add a badge with a total count of people on the list. I
created some JavaScript that would add the number of p tags together and place it in the badge. 

The following is the HTML and JavaScript I wrote for this page:

	@{
    ViewBag.Title = "SignIn";
    }


    <div class="pt-3  text-center">
        <h2 id="home-signin-headliner">Developers of TheatreCMS</h2>
        <span id="DevTotal" class="home-signin-span" data-toggle="tooltip" data-placement="right" data-animation="true" title="Number of Developers">000</span>
        <h5>SignIn</h5>
    </div>

    <div id="NameList" class="text-center">
        <p> Names go here </p>
        <p> Names go here </p>
    </div>

    <script>
        $("p").addClass("home-signin-button");

        $(function () {
            $('[data-toggle="tooltip"]').tooltip()
        })

        var parent = document.getElementById('NameList')
        var children = (parent.childNodes.length - 1) / 2;
        document.getElementById("DevTotal").innerHTML = children;
    </script>

The following is the CSS styling I created for the page. This code was inserted into the master CSS style page:

    /* Styling for Home/Signin page */
    #home-signin-headliner {
        display: inline-block;
        vertical-align: middle;
    }

    .home-signin-button {
        background-color: #fc0404;
        border: none;
        color: #fff;
        padding: 5px 10px;
        font-family: inherit;
        font-weight: bold;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        height: 35px;
        width: 275px;
        margin: 8px 8px 8px 8px;
        cursor: pointer;
        border-radius: 22px;
        transition: background-color .5s;
    }

    .home-signin-button:hover {
        background-color: #960202;
    }

    .home-signin-span {
        background-color: #fc0404;
        border: none;
        color: #fff;
        padding: 1px 1px 1px 1px;
        font-family: inherit;
        font-weight: bold;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        height: 28px;
        width: 45px;
        margin: 0px 0px 0px 4px;
        cursor: pointer;
        border-radius: 22px;
    }

*Jump to: [Page Top](#Live-Project)*

## Easy Login On Admin Navbar
This task required me to create buttons on the Admin Navbar for developers to click for automatic login. I wrote Javascript to add the appropriate user and 
password fields of a hidden form, depending on which type of user they wanted to emulate. I created a hidden form that would automatically log a developer in when 
the button was clicked. I created and styled the buttons to the specifications that the client requested. What made this a somewhat difficult task is that the 
Popout Admin Navbar needed to be functional on the actual user login page, which also used an Easy login button system. I had to create a seperate login system 
that wouldn't interfere with the Login page and create console errors.

Below is the HTML and Razor that I used to create the hidden form and buttons:

    @*Easy Login Button Form - for development purposes only. THIS MUST BE REMOVED BEFORE DEPLOYMENT*@
        @using (Html.BeginForm("Login", "Account", new { ReturnUrl = this.Request.RawUrl }, FormMethod.Post, new { role = "form", id = "Easylogin" })) // Added id="loginto be used with EasyLogin Buttons --!!! PLEASE REMOVE BEFORE DEPLOYMENT !!!
        {
            @Html.AntiForgeryToken()
            @Html.Hidden("Email", "", new { id = "EasyEmail"})
            @Html.Hidden("Password", "", new { id = "EasyPassword" })
        }

        <div class="admin_navbar_menu">
            @*Easy Login Buttons - for development purposes only. THIS MUST BE REMOVED BEFORE DEPLOYMENT*@
            <div class="text-center">
                <h4 class="mb-1">Login As...</h4>
                <p class="mb-0">
                    <input type="button" class="iconBtn" value="Admin" id="EasyAdminBtn" />
                    <input type="button" class="iconBtn" value="Subscriber" id="EasySubscriberBtn" />
                </p>
                <p class="mb-0">
                    <input type="button" class="iconBtn" value="User" id="EasyUserBtn" />
                    <input type="button" class="iconBtn" value="Cast Member" id="EasyMemberBtn" />
                </p>
            </div>

The following is the JavaScript used to auto-complete the hidden form:

    @*The JavaScript applies only to the Easy Login buttons, for the purposes of development. IT MUST BE REMOVED BEFORE DEPLOYMENT*@
        <script type="text/javascript">
            document.getElementById("EasyUserBtn").addEventListener('click', function () {
                var email = document.getElementById('EasyEmail');
                email.value = 'Userb@gmail.com';
                var pass = document.getElementById('EasyPassword');
                pass.value = '!ie12';
                document.getElementById("Easylogin").submit();
            });
            document.getElementById("EasyAdminBtn").addEventListener('click', function () {
                var email = document.getElementById('EasyEmail');
                email.value = 'tester@gmail.com';
                var pass = document.getElementById('EasyPassword');
                pass.value = 'Pass!';
                document.getElementById("Easylogin").submit();
            });
            document.getElementById("EasyMemberBtn").addEventListener('click', function () {
                var email = document.getElementById('EasyEmail');
                email.value = 'mem.test@gmail.com';
                var pass = document.getElementById('EasyPassword');
                pass.value = 'Ihcats';
                document.getElementById("Easylogin").submit();
            });
            document.getElementById("EasySubscriberBtn").addEventListener('click', function () {
                var email = document.getElementById('EasyEmail');
                email.value = 'subscriber@gmail.com';
                var pass = document.getElementById('EasyPassword');
                pass.value = '1001!';
                document.getElementById("Easylogin").submit();
            });
        </script>
        @*END Easy Login Buttons Javascript*@
    @*}*@

*Jump to: [Page Top](#Live-Project)*

## Subscription Plan Bug Fix
This task required me to fix a bug on the Admin Dashboard page. The update subscription button would throw an error if clicked because if you are logged in 
as an admin then you are not a subscriber. I was tasked to write code that would disable the button if the user is logged in as an Admin. I accomplished this 
with a bit of Razor and HTML. This was the first task I worked on in my internship. It was a great initial experience to get me up to speed with the MVC framework.

Below is the HTML and Razor that I used to disable the button if the user was logged in as Admin:

     @if (User.IsInRole("Admin"))
                    {
                        <button type="submit" class="subsave" id="subsave" disabled>Update Subscription</button>
                    }
                    else
                    {
                        <button type="submit" class="subsave" id="subsave">Update Subscription</button>
                    }

*Jump to: [List Of Stories](#Stories), [Page Top](#Live-Project)*

## Other Skills Learned
* Working with a group of developers to identify bugs and make the application more usable.
* Daily meetings to talk about the challenges of the day and to communicate any roadblocks.
* Learning new skills while writing code I was unfamiliar with. Completing the research needed in order to complete a task.
* Great practice being part of a team, and completing team programming when one developer has an issue they can not resolve.
* Becoming comfortable with the DevOps/Scrum working environment. 
* Becoming familiar using a story board. Checking out tasks and submitting them when resolved.

