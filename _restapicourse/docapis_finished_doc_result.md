---
title: Putting it all together
permalink: /docapis_finished_doc_result/
categories:
- api-doc
keywords: 
course: "Documenting REST APIs"
weight: 2.8
type: notes_docapis
---
{% include notes.html %}

## Full working example
In this example, let's pull together the various parts you've worked on to showcase the full example. I chose to format mine in Markdown syntax in a text editor.

Here's my example. 

<div class="fakePage">
<h1 id="surfreport/{beachid}">surfreport/{beachId}</h1>

<p>Returns information about surfing conditions at a specific beach ID, including the surf height, water temperature, wind, and tide. Also provides an overall recommendation about whether to go surfing. </p>

<p><code>{beachId}</code> refers to the ID for the beach you want to look up. All Beach ID codes are available from our site.</p>

<h2 id="endpoint-definition">Endpoint definition</h2>

<p><code>surfreport/{beachId}</code></p>

<h2 id="http-method">HTTP method</h2>

<p><span class="label label-primary">GET</span> </p>

<h2 id="parameters">Parameters</h2>

<table><thead>
<tr>
<th>Parameter</th>
<th>Description</th>
<th>Data Type</th>
</tr>
</thead><tbody>
<tr>
<td>days</td>
<td><em>Optional</em>. The number of days to include in the response. Default is 3.</td>
<td>integer</td>
</tr>
<tr>
<td>units</td>
<td><em>Optional</em>. Whether to return the values in imperial or metric measurements. Imperial will use feet, knots, and fahrenheit. Metric will use centimeters, kilometers per hour, and celsius.</td>
<td>string</td>
</tr>
<tr>
<td>time</td>
<td><em>Optional</em>. If you include the time, then only the current hour will be returned in the response.</td>
<td>integer. Unix format (ms since 1970) in UTC.</td>
</tr>
</tbody></table>

<h2 id="sample-request">Sample request</h2>

{% highlight bash %}
curl --get --include 'https://simple-weather.p.mashape.com/surfreport/123?units=imperial&days=1&time=1433772000' 
  -H 'X-Mashape-Key: WOyzMuE8c9mshcofZaBke3kw7lMtp1HjVGAjsndqIPbU9n2eET' 
  -H 'Accept: application/json'
{% endhighlight %}

<h2 id="sample-response">Sample response</h2>

{% highlight json %}
{
    "surfreport": [
        {
            "beach": "Santa Cruz",
            "monday": {
                "1pm": {
                    "tide": 5,
                    "wind": 15,
                    "watertemp": 80,
                    "surfheight": 5,
                    "recommendation": "Go surfing!"
                },
                "2pm": {
                    "tide": -1,
                    "wind": 1,
                    "watertemp": 50,
                    "surfheight": 3,
                    "recommendation": "Surfing conditions are okay, not great."
                },
                "3pm": {
                    "tide": -1,
                    "wind": 10,
                    "watertemp": 65,
                    "surfheight": 1,
                    "recommendation": "Not a good day for surfing."
                }
            }
        }
    ]
}
{% endhighlight %}

<p>The following table describes each item in the response.</p>

<table><thead>
<tr>
<th>Response item</th>
<th>Description</th>
</tr>
</thead><tbody>
<tr>
<td><strong>beach</strong></td>
<td>The beach you selected based on the beach ID in the request. The beach name is the official name as described in the National Park Service Geodatabase.</td>
</tr>
<tr>
<td><strong>{day}</strong></td>
<td>The day of the week selected. A maximum of 3 days get returned in the response.</td>
</tr>
<tr>
<td><strong>{time}</strong></td>
<td>The time for the conditions. This item is only included if you include a time parameter in the request.</td>
</tr>
<tr>
<td><strong>{day}/{time}/tide</strong></td>
<td>The level of tide at the beach for a specific day and time. Tide is the distance inland that the water rises to, and can be a positive or negative number. When the tide is out, the number is negative. When the tide is in, the number is positive. The 0 point reflects the line when the tide is neither going in nor out but is in transition between the two states.</td>
</tr>
<tr>
<td><strong>{day}/{time}/wind</strong></td>
<td>The wind speed at the beach, measured in knots per hour or kilometers per hour depending on the units you specify. Wind affects the surf height and general wave conditions. Wind speeds of more than 15 knots per hour make surf conditions undesirable, since the wind creates white caps and choppy waters.</td>
</tr>
<tr>
<td><strong>{day}/{time}/watertemp</strong></td>
<td>The temperature of the water, returned in Farenheit or Celsius depending upon the units you specify. Water temperatures below 70 F usually require you to wear a wetsuit. With temperatures below 60, you will need at least a 3mm wetsuit and preferably booties to stay warm.</td>
</tr>
<tr>
<td><strong>{day}/{time}/surfheight</strong></td>
<td>The height of the waves, returned in either feet or centimeters depending on the units you specify. A surf height of 3 feet is the minimum size needed for surfing. If the surf height exceeds 10 feet, it is not safe to surf.</td>
</tr>
<tr>
<td><strong>{day}/{time}/recommendation</strong></td>
<td>An overall recommendation based on a combination of the various factors (wind, watertemp, surfheight). Three responses are possible: (1) &quot;Go surfing!&quot;, (2) &quot;Surfing conditions are okay, not great&quot;, and (3) &quot;Not a good day for surfing.&quot; Each of the three factors is scored with a maximum of 33.33 points, depending on the ideal for each element. The three elements are combined to form a percentage. 0% to 59% yields response 3, 60% - 80% and below yields response 2, and 81% to 100% yeilds response 3.</td>
</tr>
</tbody></table>

<h2 id="error-and-status-codes">Error and status codes</h2>

<p>The following table lists the status and error codes related to this request.</p>

<table><thead>
<tr>
<th>Status code</th>
<th>Meaning</th>
</tr>
</thead><tbody>
<tr>
<td>200</td>
<td>Successful response</td>
</tr>
<tr>
<td>400</td>
<td>Bad request -- one or more of the parameters was rejected.</td>
</tr>
<tr>
<td>4112</td>
<td>The beach ID was not found in the lookup.</td>
</tr>
</tbody></table>

<h2 id="code-example">Code example</h2>

<p>The following code samples shows how to use the surfreport endpoint to get the surf conditions for a specific beach. In this case, the code is just showing the overall recommendation about whether to go surfing.</p>

{% highlight html %}
<!DOCTYPE html>
<html>
<head>
<script src="http://code.jquery.com/jquery-2.1.1.min.js"></script>
  <meta charset="utf-8">
  <title>API Weather Query</title>
  <script>

  function getSurfReport() { 

// use AJAX to avoid CORS restrictions in API calls.
 var output = $.ajax({
    url: 'https://simple-weather.p.mashape.com/surfreport/123?units=imperial&days=1&time=1433772000', 
    type: 'GET', 
    data: {}, 
    dataType: 'json',
    success: function(data) {
        //Here we pull out the recommendation from the JSON object.
        //To see the whole object, you can output it to your browser console using console.log(data);
        document.getElementById("output").innerHTML = data.surfreport[0].monday.2pm.recommendation; 
        },
    error: function(err) { alert(err); },
    beforeSend: function(xhr) {
    xhr.setRequestHeader("X-Mashape-Authorization", "WOyzMuE8c9mshcofZaBke3kw7lMtp1HjVGAjsndqIPbU9n2eET"); // Enter here your Mashape key
    }
});
	
}
 
</script>
</head>
<body>
{% endhighlight %}

<p>In this example, the <code>ajax</code> method from jQuery is used because it allows cross-origin resource sharing (CORS) for the weather resources. In the request, you submit the authorization through the header rather than directly in the endpoint path. The endpoint limits the days returned to 1 in order to increase the download speed.</p>

<p>For simple demo purposes, the response is assigned to the <code>data</code> argument of the success method, and then written out to the <code>output</code> tag on the page. We&#39;re just getting the surfing recommendation, but there&#39;s a lot of other data you could choose to display.</p>

</div>

## Markdown syntax

Markdown provides an easy syntax for creating HTML. To view the the Markdown formatting for this content, see the <a href="{{ "/files/restapicourse/surfreportendpointdoc.md" | prepend: site.baseurl}}">surfreportendpointdoc.md</a>.

## Structure and templates

If you have a lot of endpoints to document, you'll probably want to create templates that follow a common structure. 

Additionally, if you want to add a lot of styling to each of the elements, you may want to push each of these elements into a template by way of a script. I'll talk more about publishing in the next course, Publishing API Documentation.
