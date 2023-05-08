Download Link: https://assignmentchef.com/product/solved-sdev300-lab04
<br>
<strong>PHP Form processing </strong>

<h1>Overview</h1>

This lab walks you through using PHP to create simple Web applications that use forms to gather information from a user. In addition, the important topic of sessions is demonstrated.

<h1>Learning Outcomes</h1>

At the completion of the lab you should be able to:

<ol>

 <li>Create, and test PHP scripts to process HTML Forms</li>

 <li>Compare and contrast session creating mechanisms in PHP</li>

</ol>

<strong> </strong>

<h1>Lab Submission Requirements</h1>

After completing this lab, you will submit a word (or PDF) document that meets all of the requirements in the description at the end of this document. In addition, your PHP files should be submitted. You should submit multiple files in a zip file.

<strong> </strong>

<h1>Virtual Machine Account Information</h1>

Your Virtual Machine has been preconfigured with all of the software you will need for this class. You have connected to this machine in the previous labs. Reconnect again using the Remote Desktop connection, your Administrator username and password.




<h1>Part 1 – Create and test PHP scripts to process HTML Forms</h1>

In this exercise we will create PHP web pages that include simple forms that use GET and POST methods for submission of data.  The GET method is used to request data from a specified resource whereas the POST method is used to send data to a server. The first set of code below is the HTML file using three Text input fields and a PHP GET method.




<ol>

 <li>Copy and paste the following code into a file named DemoGetForm.html in the SDEV300 folder on your AWS Cloud VM.</li>

</ol>




&lt;html&gt;

&lt;head&gt;&lt;title&gt;Simple Form with Get Method &lt;/title&gt;

&lt;/head&gt; &lt;body&gt;

&lt;h1&gt; Please complete the Form &lt;/h1&gt;

&lt;form action=”getSubmit.php” method=”get”&gt;

First name: &lt;input type=”text” name=”fname”&gt;&lt;br&gt;

Last name: &lt;input type=”text” name=”lname”&gt;&lt;br&gt;

Password: &lt;input type=”password” name=”mypass”&gt;&lt;br&gt;

&lt;input type=”submit” value=”Submit”&gt;

&lt;/form&gt;

&lt;/body&gt;

&lt;/html&gt;




Notice this is an HTML file with form fields similar to those created in a previous lab exercise. However; the action “getSubmit.php” and the method=”get” provide the uniqueness and real functionality of this form. When data is entered into the Text fields and a user clicks on the Submit button, the data is processed by the getSubmit.php using the HTTP GET method process.

Next, we will create the getSubmit.php file used to process the form.

<ol start="2">

 <li>Create an additional file that will be used to process the HTML form that is submitted. The file should be named getSubmit.php and be placed in same location as the HTML file. The file should contain these contents:</li>

</ol>




&lt;!– HTML Forms with Get Submit

Date: Jan 01, XXXX

Author: Dr. Robertson

Title: getSubmit.php

description: Demo how to retrieve Form data

–&gt;

&lt;html&gt;

&lt;head&gt;

&lt;meta http-equiv=”Content-Type” content=”text/html; charset=UTF-8″&gt;

&lt;title&gt;Get Form Echo&lt;/title&gt;

&lt;/head&gt;

&lt;body&gt;




&lt;?php

// Retrieve Data using GET method




<table width="40">

 <tbody>

  <tr>

   <td width="40">$_GET$_GET</td>

  </tr>

 </tbody>

</table>

$fname = [“fname”];

$lname = [“lname”];

$mypassword = $_GET[“mypass”];




// Display in a table              echo “&lt;h3&gt; Form Data &lt;/h3&gt;”;        echo “&lt;table border=’1′&gt;”;        echo “&lt;tr&gt;

&lt;th&gt;Firstname&lt;/th&gt;

&lt;th&gt;Lastname&lt;/th&gt;

&lt;th&gt;Password&lt;/th&gt;              &lt;/tr&gt;”;        echo “&lt;tr&gt;

&lt;td&gt;$fname&lt;/td&gt;

&lt;td&gt;$lname&lt;/td&gt;

&lt;td&gt;$mypassword&lt;/td&gt;

&lt;/tr&gt;”;        echo “&lt;/table&gt;”;




?&gt;

&lt;/body&gt;

&lt;/html&gt;







Several key components are found in this PHP file that make the Web application dynamic. Note the following common functionality and elements in a PHP form processing file:

<ol>

 <li>The names of the Text fields and other HTML form fields found in the HTML file are used to retrieve the data entered in the form by the user. Notice in this case, the text fields named “fname” and “lname” are the names associated the the $_GET method (e.g.</li>

</ol>

$_GET[“fname”]). Be sure to appropriately name those attributes when creating your PHP file.

<ol>

 <li>You can use any acceptable and appropriate PHP variable to assign the values of the GET (or POST) methods. For example, the code assigned $fname to the GET[“fname”] value.</li>

 <li>Once you have the values from the form, you can process as needed. In this example, the results were just displayed in HTML table. However; you could store the data in database, send the data to another location or one of nearly infinite other tasks.</li>

 <li>Use <strong>echo</strong> to encode HTML code. Notice echo starts the line and then quotes are used to enclose the HTML table code. (e.g. echo “&lt;table border=’1′&gt;”;)</li>

 <li>Note that quotes within double quotes should use single quotes for correctly processing the</li>

</ol>

HTML attributes. “&lt;table border=’1′&gt;”;)

<ol>

 <li>Any valid HTML code can be embedded within the PHP code including style sheets and JavaScript code. However; be careful with interlacing too much as the code does become difficult to maintain and debug.</li>

</ol>




<ol start="3">

 <li>Launch the HTML file from your localhost/SDEV300 folder. Enter your firstname, lastname and some text for a password in the form as shown in Figure 1.</li>

</ol>




<em>Figure 1 Entering Data in the Form </em>

<ol start="4">

 <li>Press the Submit button and the form data you entered will be echoed to the display as shown in figure 2.</li>

</ol>




<em>Figure 2 Get Submit Results </em>




As you review the code and results, notice the query string sent at the URL provides all of the field parameters and their values. Also, notice this is in clear text and very insecure.




http://localhost/SDEV300/getSubmit.php?fname=Jimmy&amp;lname=Robertson&amp;mypass=234111




When you see this query string it is a clear sign, the GET method was used. Sending passwords or other sensitive information using the GET method is never recommended and a sure way to have your Web application hacked very quickly.







<ol start="5">

 <li>To compare with the Post method create two additional files using the following code:</li>

</ol>

HTML file: DemoPostForm.html

&lt;html&gt;

&lt;head&gt;&lt;title&gt;Simple Form with Post Method &lt;/title&gt;

&lt;/head&gt;

&lt;body&gt;

&lt;h1&gt; Please complete the Form &lt;/h1&gt;

&lt;form action=”postSubmit.php” method=”post”&gt;

First name: &lt;input type=”text” name=”fname”&gt;&lt;br&gt;

Last name: &lt;input type=”text” name=”lname”&gt;&lt;br&gt;

Password: &lt;input type=”password” name=”mypass”&gt;&lt;br&gt;

&lt;input type=”submit” value=”Submit”&gt;

&lt;/form&gt;

&lt;/body&gt;

&lt;/html&gt;













PHP file: postSubmit.php




&lt;!– HTML Forms with Post Submit

Date: Jan 01, XXXX

Author: Dr. Robertson  Title: postSubmit.php

description: Demo how to retrieve Form data

–&gt;

&lt;html&gt;

&lt;head&gt;

&lt;meta http-equiv=”Content-Type” content=”text/html; charset=UTF-8″&gt;

&lt;title&gt;Get Form Echo&lt;/title&gt;

&lt;/head&gt;

&lt;body&gt;

&lt;?php

// Retrieve Data using Post method

<table width="48">

 <tbody>

  <tr>

   <td width="48">$_POST$_POST</td>

  </tr>

 </tbody>

</table>

$fname = [“fname”];

$lname = [“lname”];

$mypassword = $_POST[“mypass”];         // Display in a table              echo “&lt;h3&gt; Form Data &lt;/h3&gt;”;        echo “&lt;table border=’1′&gt;”;        echo “&lt;tr&gt;

&lt;th&gt;Firstname&lt;/th&gt;

&lt;th&gt;Lastname&lt;/th&gt;

&lt;th&gt;Password&lt;/th&gt;              &lt;/tr&gt;”;        echo “&lt;tr&gt;

&lt;td&gt;$fname&lt;/td&gt;

&lt;td&gt;$lname&lt;/td&gt;

&lt;td&gt;$mypassword&lt;/td&gt;

&lt;/tr&gt;”;        echo “&lt;/table&gt;”;




?&gt;

&lt;/body&gt;

&lt;/html&gt;




When comparing the POST method to the GET method files, notice the only real differences in code are the use of the  “POST” as opposed to “GET”. For example, for the postSubmit.php code, the data is retrieved using the following code for the $lname variable:

$lname = $_POST[“lname”];




Also notice the form attributes in the DemoPostForm.html file contains the following line of code with the POST method:

&lt;form action=”postSubmit.php” method=”post”&gt;




<ol start="6">

 <li>Launch and run the application and note the output display as shown in figures 3 and 4.</li>

</ol>




<em>Figure 3 Running the HTTP Post </em>

To send the data to for processing click on the “Submit” button.

As shown in figure 4, the end results are the same where the data entered in the form is echoed in the display. However; in this case the URL does not contain the clear text password:

http://localhost/SDEV300/postSubmit.php







<em>Figure 4 Post Results </em>




As you will see in some of security analysis we perform with the OWASP ZAP tool later in this course, the post method isn’t necessarily more secure but at least the URL doesn’t display the sensitive data in a query string. This offers some advantages particularly in keeping your access logs more secure with less sensitive information. For example, compare the following two lines found in the access.log file in the logs area for the Apache server:




[18/May/2018:14:51:38 +0000] “GET

/SDEV300/getSubmit.php?fname=Jimmy&amp;lname=Robertson&amp;mypass=234111 HTTP/1.1”

200 332




[19/May/2018:13:57:00 +0000] “POST /SDEV300/postSubmit.php HTTP/1.1” 200 338

Clearly, the second line is more appropriate and more secure as the password is not available in the log files.




<h1>Part 2 – Compare and contrast session creating mechanisms in PHP</h1>

In this exercise we will create a simple PHP page that creates and reads available cookies as well as PHP session variables. For the first session example, we will create a cookie in PHP and use a form based submission to expire the cookie.




HTTP, by default is stateless. This means as a person navigates a Web page or even submits data via forms or other mechanism, once the user leaves that page, the state, and other information about what the use has done or requested is no longer available. Cookies and sessions provide a mechanism to add state to the interaction with a user to make the experience more personal.




The Mozilla site defines a cookie as “A small piece of data that a server sends to the user’s web browser.  The browser may store it and send it back with the next request to the same server“.  Ultimately, cookies help an application determine if requests come from the same browser.




Sessions are similar to cookies but often provide tokens or some specific identifier to preserve certain data across subsequent accesses. This allows the developer to build more customized applications enhancing the interactivity and personalization of the web site. PHP and most other languages has session methods that support this functionality.




As you can imagine, starting and correctly stopping sessions is critical in web application security. For example, imagine if a user logs into a web application on a public computer and forgets to terminate their session. Then, another use logs in and the application still believes the first user is still logged in and provides private or sensitive information. Clearly, much caution and meticulous testing must take place to ensure sessions are secure and not hijacked by someone else.







<ol>

 <li>Copy and paste the following code into a file named DemoCookies.php in your AWS Cloud VM in your SDEV300 folder.</li>

</ol>




&lt;!– PHP and Cookies

Date: Jan 01, XXXX

Author: Dr. Robertson

Title: DemoCookies.php

description: Demo how to use Cookies with PHP

–&gt;

&lt;!DOCTYPE html&gt;

&lt;html&gt;

&lt;head&gt;

&lt;title&gt;Cookies Demo &lt;/title&gt;

&lt;/head&gt;

&lt;body&gt;

&lt;h1&gt;PHP Cookies Demo &lt;/h1&gt;

&lt;?php

$cookie_name = “UMUCGamer”;

$cookie_value = “CMSC325”;

// Set cookie for 7 days

setcookie($cookie_name, $cookie_value, time() + (86400 * 30), “/”);

// Check for cookie

if(!isset($_COOKIE[$cookie_name])) {

echo $cookie_name . “,” . $cookie_value . “‘ is not set!”;

} else {

echo “Welcome back” . $cookie_name . “-” . $_COOKIE[$cookie_name];




}

?&gt;

&lt;/br&gt;

&lt;!– Form to expire cookie –&gt;

&lt;form action=”expireCookie.php” method=”post”&gt;

&lt;input type=”submit” value=”Expire Cookie”&gt;

&lt;/form&gt;




&lt;/body&gt;

&lt;/html&gt;




There are multiple code components related to managing cookies in this example worth mentioning:

<ol>

 <li>The setcookie() method is used to set the name, value and expiration time. In this example, a cookie named UMUCGamer was set with a value of CMSC325 and an expiration time of 30 days from the current time. (86400 seconds = 1 day). The “/” denotes the path where the cookie is available. The “/” denotes the entire domain. (In this case, localhost)</li>

 <li>The isset() method is used to determine if the cookie is set. The if logic is then used to take action. So in this case, messages are displayed based on if the cookie is set.</li>

 <li>Finally, a form is provided with a single button that will expire the cookie. Keep in mind, in this case, the cookie, once set was enabled for 30 days. The expire cookie will remove it sooner if needed.</li>

</ol>

Cookies are quite handy in advertising or determining is a particular visits site quite regularly.




<ol start="2">

 <li>Create an additional file that will be respond when the Expire Cookie button is selected. The file should be named expireCookie.php and be placed in same location as the HTML file. The file should contain these contents:</li>

</ol>




&lt;html&gt;

&lt;head&gt;&lt;title&gt;Expire the cookies &lt;/title&gt;

&lt;/head&gt;

&lt;body&gt;

&lt;?php

// Expire the cookie $cookie_name = “UMUCGamer”; if(isset($_COOKIE[$cookie_name])) {

setcookie( $cookie_name, “”, time() – 3600, “/” );  echo “Expiring the cookie: ” . $cookie_name;

} else {

echo “Cookie not found to expire “;

}

?&gt;

&lt;h2&gt; Thanks for playing with PHP cookies &lt;/h2&gt;

&lt;/body&gt;

&lt;/html&gt;




In the expire cookie PHP code, the isset() method is used to determine if a particular cookie is set. If it is the expiration time is expired by setting the expiration time to the current time less one hour (3600 seconds). If the cookie was already expired or not found, an appropriate message is displayed.




<ol start="3">

 <li>Launch the HTML file. Cookies can be challenging to work with, because they often linger beyond their actual expiration date. This does have security implications which we will touch on through this program. When launching the application for the first time, the cookie has not been set. (See figure 5).</li>

</ol>







<em>Figure 5 DemoCookies PHP Initial Run </em>

As shown in figure 6, when you refresh the browser and open it again, the cookie will be present as indicated by the welcome back message.




<em>Figure 6 Refreshing or reloading the page shows the cookie was set </em>

We would need to wait 30 days (with our current settings) to have the cookie expire. However; if you select the “Expire Cookie” button and refresh the browser, the cookie will no longer be present. (See figures 7 and 8)




<em>Figure 7 Expiring the cookie </em>




<em>Figure 8 The cookie was expired </em>




You should experiment with the cookie code by setting different expiration times to verify the performance and limitations of using cookies. If you visit a site, that uses cookies (which most do) you will often receive an informational note that the site uses cookies. This is required by developers to be in compliant with certain (and recent) privacy laws.




<ol start="4">

 <li>Next, we will look at the Sessions options in PHP. In this example, we will create 3 files. An html file will be used to input a username and email address using an html form. Upon submitting the form, a PHP file will start a session and store the username and email address in session variables. Finally, an option to logout and unset the stored session variables will be provided in a logout.php file.</li>

</ol>

Session variables are more commonly used than cookies for maintaining state in Web applications. However; they can be dangerous from a security perspective since often browsers do not properly remove these variables immediately. This is why you often see a note from the site, to completely close the browser after ending your session.

The files created for this demonstration of session variables will be named loginAuth.html, authcheck.php and logout.php; respectively.

File: loginAuth.html

&lt;html&gt;

&lt;head&gt;

&lt;meta http-equiv=”Content-Type” content=”text/html; charset=UTF-8″&gt;    &lt;title&gt;Form Login&lt;/title&gt;

&lt;/head&gt;




&lt;body OnLoad=”document.main.username.focus();”&gt;







&lt;table &gt;

&lt;tr&gt;

&lt;td colspan=”2″&gt;

&lt;h4&gt;Enter your Username and Email Address to continue&lt;/h4&gt;

&lt;/td&gt;

&lt;/tr&gt;

&lt;!– create the main form with an input text boxes –&gt;

&lt;form name=”main” method=”post” action=”authcheck.php”&gt;

&lt;tr&gt;

&lt;td&gt;username:&lt;/td&gt;

&lt;td&gt;&lt;input name=”username” type=”text” size=”50″&gt;&lt;/td&gt;

&lt;/tr&gt;

&lt;tr&gt;

&lt;td&gt;Email Address:&lt;/td&gt;

&lt;td&gt;&lt;input name=”emailadd” type=”text” size=”50″&gt;&lt;/td&gt;

&lt;/tr&gt;

&lt;tr&gt;

&lt;td colspan=”2″ align=”center”&gt;&lt;input name=”btnsubmit” type=”submit” value=”Submit”&gt;&lt;/td&gt;

&lt;/tr&gt;

&lt;/table&gt;

&lt;/form&gt;




&lt;/body&gt;

&lt;/html&gt;




In the loginAuth.html file, a simple login form requesting the use to enter the username and email address.  Notice the form uses a HTTP POST method with the resulting action of “authcheck.php”.

One additional note is JavaScript was used to focus the user on the username field of the main form. We haven’t covered JavaScript but you will see quite a bit of JavaScript code intermingled in HTML (and PHP) code. It is fairly easy to use as is it is object-based and has a good reference manual at the Mozilla web site. In this case, the object-based notation of onLoad=”document.main.username.focus();” is just instructing that when the page is loaded, focus on the main.username field of the form. The document object always refers to the entire page. Note JavaScript is not Java code, although some syntax is similar.

If you are interested in learning more about Javascript, check out this developer reference:

<a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript">https://developer.mozilla.org/en</a><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript">–</a><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript">US/docs/Web/JavaScript</a>




File: authcheck.php

&lt;html&gt;

&lt;head&gt;

&lt;meta http-equiv=”Content-Type” content=”text/html; charset=UTF-8″&gt;     &lt;title&gt;User Authenticate &lt;/title&gt;

&lt;/head&gt;

&lt;body&gt;




&lt;?php

// Retrieve Post Data

$username = $_POST[“username”];

$email = $_POST[“emailadd”];




// Set the session information            session_start();

$_SESSION[‘appusername’] = $username;

$_SESSION[‘appemail’] = $email;




// Display the Session information  echo “&lt;h3&gt; Session Data  &lt;/h3&gt;”; echo “&lt;table border=’1′&gt;”; echo “&lt;tr&gt;

&lt;td&gt;Username &lt;/td&gt;

&lt;td&gt; Email &lt;/td&gt;

&lt;/tr&gt;”; echo “&lt;tr&gt;

&lt;td&gt;” . $_SESSION[‘appusername’] . “&lt;/td&gt;”; echo  “&lt;td&gt;” . $_SESSION[‘appemail’]. “&lt;/td&gt;”; echo   “&lt;/tr&gt;”;       echo “&lt;/table&gt;”;




// Provide a button to logout




echo “&lt;form name=’logout’ method=’post’ action=’logout.php’&gt;

&lt;input name=’btnsubmit’ type=’submit’ value=’Logout’&gt;

&lt;/form&gt;”;

?&gt;

&lt;/body&gt;

&lt;/html&gt;




The authcheck.php file takes the two POST variables from the HTML submit and sets two session variables in PHP. A couple of comments about this code:

<ol>

 <li>The session_start(); call must be used for all PHP files that require session use. Even if a previous file used session_start(); subsequest PHP files that request session values must use that call as well.</li>

 <li>Use $_SESSION[]to set a session value where the name of the session variable is specifically listed in the []. For example, $_SESSION[‘appusername’] = $username; In this case, the value in the $username is assigned to the Session variable named appusername.</li>

 <li>At the end of the code, a form (that calls logout.php) is used to unset the session variables. It is critical all session based web applications have a logout option.</li>

</ol>

By default, the PHP session timeout is 30 minutes.

File: logout.php

&lt;html&gt;

&lt;head&gt;

&lt;meta http-equiv=”Content-Type” content=”text/html; charset=UTF-8″&gt;    &lt;title&gt;Form Login&lt;/title&gt;

&lt;/head&gt;

&lt;?php session_start();

unset($_SESSION[‘appusername’]); unset($_SESSION[‘appemail’]);







// Display the Session information echo “&lt;h3&gt; Session Data after Logout  &lt;/h3&gt;

&lt;table border=’1′&gt;

&lt;tr&gt;

&lt;td&gt;Username &lt;/td&gt;

&lt;td&gt; Email &lt;/td&gt;

&lt;/tr&gt;

&lt;tr&gt;

&lt;td&gt;” . $_SESSION[‘appusername’] . “&lt;/td&gt;” .

“&lt;td&gt;” . $_SESSION[‘appemail’] . “&lt;/td&gt;

&lt;/tr&gt;

&lt;/table&gt;”;

?&gt;




&lt;/body&gt;

&lt;/html&gt;




The logout.php file uses the unset() method to unset the appusername, and appemail session variables. Then the values are displayed (which should now be null) in an HTML table.  Notice, the session_start() was called prior to unsetting the session variables.

<ol start="5">

 <li>Run loginAuth.html from your localhost/SDEV300 folder in your AWS Cloud VM Browser as shown in figure 9.</li>

</ol>




<em>Figure 9 Enter Username and Email </em>

After typing in your username and email address click on “Submit”. As shown in figure 10, the check will set the session variables and show their current values.




<em>Figure 10 Display the Session Variables </em>




<ol start="6">

 <li>Click on “logout” to unset the session variables. (See figure 11).</li>

</ol>







<em>Figure 11 Unset the Session Variables </em>

You should experiment with the code to learn more about session variables. Be sure to add more session variables and test with additional PHP code that uses the isset() method to check for the presence of session variables.

The isset() check is critical in checking for session variable for displaying a PHP page. For example, you don’t want a customer to directly jump to a Products pages without logging in. So, you must only show the Products page if first check to see if the PHP session variables are set. If they are not set, you must redirect them to the login page.

The following PHP provide similar functionality to what would be needed:

session_start();




// check for valid login if (!isset($_SESSION[‘username’])

{ // Send to login      include(‘login.php’);

}

else  // Session is Okay. Let ‘em in

{

// Code here to display the Products Page

}




<strong> </strong>

<strong>Lab submission details: </strong>

As part of the submission for this Lab, you will create your own unique PHP Web application to store and use session variables in a simple project management application. <strong>You must use the AWS Cloud VM for this exercise. </strong>

Specifically, you will create a <strong>unique </strong>Project Management application using PHP and HTML that allows a user to login to a website, check the progress of a specific project and provide feedback about the progress.

The following guidelines should be used in your design and development:

<ol>

 <li>The Login form should consist of fields for username, email address and a password.</li>

 <li>After login, a personal welcome message should appear along with a list of several projects (at least 10) your company is working on and the current percent completion of each project.</li>

 <li>The display should include the ability for the customer that logged in to provide comments about one or more of the projects and submit those comments.</li>

 <li>A customer can remain on the site for up to 30 minutes, without activity, before the session will expire.</li>

 <li>Once all comments are provided, the customer should be able to submit their comments and a summary page showing all of the project information plus the customer comments will result. The customer should be able to add as many comments as they like for each project. (Hint: use a textarea)</li>

 <li>The summary page should include every project available regardless of whether comments were provided or not.</li>

 <li>The summary page should include a “Thank you” message at the top as well along with the project data and customer comments and date and time the comments were submitted.</li>

 <li>Each PHP page should provide the ability for the customer to logout at any time.</li>

</ol>

The following is a possible mock-up of what a page might look like for listing projects and providing customer feedback.

<table width="534">

 <tbody>

  <tr>

   <td width="270">Login</td>

   <td width="264">Logout</td>

  </tr>

 </tbody>

</table>




Welcome John. Please add comments in the last column of the table below and press Submit when ready to review your comments.

<table width="623">

 <tbody>

  <tr>

   <td width="208">Project</td>

   <td width="208">% complete</td>

   <td width="208">Customer Comments:</td>

  </tr>

  <tr>

   <td width="208">SpaceX</td>

   <td width="208">35%</td>

   <td width="208"> </td>

  </tr>

  <tr>

   <td width="208">Mission to Mars</td>

   <td width="208">15%</td>

   <td width="208"> </td>

  </tr>

  <tr>

   <td width="208">PHP Into</td>

   <td width="208">65%</td>

   <td width="208"> </td>

  </tr>

  <tr>

   <td width="208">…</td>

   <td width="208"> </td>

   <td width="208"> </td>

  </tr>

 </tbody>

</table>




Submit

When the customer selects “Submit” they should see the personal thank you and the project data and any comments they added for that submission. Note, you do not store the comments in session variables. Assume a refresh occurs for each submission. However; you should store appropriate session variable for the login and make sure the customer has appropriately logged in before displaying the projects for comment.

Feel free to add additional HTML and PHP elements to enhance your web application. Create screen captures showing the successful running of your application. Describe each screen capture to explain the results of your application.

For your deliverables, you should submit a zip file containing your word document (or PDF file) with screen shots of the application running successfully along with your PHP web application file and the access.log file.

You should include the Apache log file. <strong>Submissions without access.log files will not be accepted. </strong>

Include your full name, class number, professor name, and section and date in the document.










<strong>Grading Rubric: </strong>

<table width="648">

 <tbody>

  <tr>

   <td width="126"><strong>Attribute </strong></td>

   <td width="522"><strong>Meets </strong></td>

  </tr>

  <tr>

   <td width="126">PHP App</td>

   <td width="522"><strong>75 points </strong>The Login form includes fields for username, email address and a password. (5 points) After login, a personal welcome message should appear along with a list of several projects (at least 10) your company is working on and the current percent completion of each project. (10 points) The display should include the ability for the customer that logged in to provide comments about one or more of the projects and submit those comments. (10 points) Stores appropriate session variable for the login and makes sure the customer has appropriately logged in before displaying the projects for comment. (10 points) A customer can remain on the site for up to 30 minutes, without activity, before the session will expire. (10 points) Once all comments are provided, the customer should be able to submit their comments and a summary page showing all of the project information plus the customer comments will result. The customer should be able to add as many comments as they like for each project. (Hint: use a textarea) (10 points) The summary page should include every project available regardless of whether comments were provided or not. (5 points) </td>

  </tr>

  <tr>

   <td width="126"> </td>

   <td width="522">The summary page should include a “Thank you” message at the top as well along with the project data and customer comments and date and time the comments were submitted. (5 points) Each PHP page should provide the ability for the customer to logout at any time. (10 points) <strong>Does not include access.log (-100) </strong><strong>Does not use the SDEV AMI. (-100)</strong><strong> </strong></td>

  </tr>

  <tr>

   <td width="126">Documentation and submission</td>

   <td width="522"><strong>25 points </strong>Submits a winzip file containing your word document with screen captures and access.log, html files, image files, PHP files and other required Web application files. (10 points)<strong> </strong>Includes labeled, screen captures of the AWS Cloud VM running the Web/PHP page. Screen captures are described with VM IP address clearly visible. (10 points) Title page includes your full name, class number and section, date and the professor’s name. Document is neat, well-organized and free from spelling and grammar errors. (5 points)</td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<strong> </strong>