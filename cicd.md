---
layout: page
title: CICD - Primer
---
<div class="col-lg-12 text-center">
	<h2 class="section-heading text-uppercase">Privacy Policy</h2>
</div>

This Privacy Policy describes how your personal information is collected, used, and shared when you visit {{ site.title }} (the “Site”).

**Path To CICD**

You are not required to input an email, however, if you do, you will receive an email once the project is ready with names and locations for the project files.

<form onSubmit="generateProject()">
  <label for="projectName">Project Name:</label>
  <input type="text" id="projectName" name="projectName"><br><br>
  <label for="groupId">Group Id:</label>
  <input type="text" id="groupId" name="groupId"><br><br>
   <label for="email">Email:</label>
  <input type="text" id="email" name="email"><br><br>
  <input type="submit" value="Submit">
</form>


<script>
function generateProject() {
  var xhttp = new XMLHttpRequest();
  var projectName = document.getElementById("projectName").value;
  var groupId = document.getElementById("groupId").value;
  xhttp.open("GET", "http://172.19.121.77:8080/job/generate-project-pipeline/buildWithParameters?token=1122a448df430a8c36dc8b159cb4bb7356&group=" + groupId + "&projectName=" + projectName, true);
  xhttp.send();
}
</script>

{% if site.analytics.google %}

Automatically Collected (Google Analytics):

When you visit the Site, we automatically receive information about your device from your browser, such as your IP address. As you browse the Site, we also collect information about how you interact with the Site. We refer to this automatically-collected information as “Device Information”.

We collect Device Information using cookies. “Cookies” are data files that are placed on your device. For more information about cookies and how to disable them, visit http://www.allaboutcookies.org.

We do this using Google Analytics: <https://www.google.com/intl/en/policies/privacy/>.

You can opt-out of Google Analytics here: <https://tools.google.com/dlpage/gaoptout>.

{% else %}

We do not collect any data about you or use any cookies.

{% endif %}

**CHANGES**

We may update this privacy policy from time to time for personal, operational, legal, or regulatory reasons.

**CONTACT US**

For more information about our privacy practices or if you have questions, please contact us by email at <a href="mailto:{{ site.email }}">{{ site.email }}</a>.
