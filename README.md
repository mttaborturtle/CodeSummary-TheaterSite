# Live Project

## Introduction
In the last two weeks of my time with the Tech Academy, I worked with a team to develop a full scale Code First MVC Web Application in C#. 
Working on a legacy application gave me a great learning oppertunity to work out existing bugs, creating new elements, and adding completely new 
features to make the web application better as well as a more positive user experience. We delivered all needed changes in a timely fashion and met our 2 
week deadline. In my experience with the team I learned how a good software developer works in a team setting, and there were many examples of 
great leadership from the instructors. I worked on several stories both front-end and back-end, and I am very proud of my code accomplishments. 
Everyone on the team had the chance to work on stories in both front/back-end of various difficulty levels. My final story was of a high level 
of difficulty and I am the most proud of that work. I'm confident I will use the skills I learned that are featured here for many years to come.

## Sign-In Page Styling
In this story I took an existing basic and non-styled page and made it into a beautifully designed and visual appealing page. The names are added by students
as the firs thing they do when they Join the live project. They add their name by creating a new p tag with their name in it. I had to style it in a way that
the sign in procedure would be simple for the new developers signing in, in other words I couldn't add tags or styles to the individual p tags. I had to find a 
way to style the tags without changing the code entered by the developers signing in. I also was tasked to add a badge with a total count of people on the list. I
created some JavaScript that would add the number of p tags together and place it in the badge. You can see this code in the clip below.

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

The following is the CSS styling I created for the page. This code was inserted into the master CSS style page.

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



 [back end stories](#back-end-stories) [front end stories](#front-end-stories)  [skills](#other-skills-learned) 