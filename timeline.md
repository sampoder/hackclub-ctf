---
title: Timeline
layout: default
---
<p style = "text-align: center">
Here's a schedule of events! Times are in EDT unless otherwise noted.
</p>
<div class="row section" style = "padding-top: 5px">
<div id="events"></div></div>
    
<script>
    try {
    var xhttp = new XMLHttpRequest();
    xhttp.onreadystatechange = function() {
        if (this.readyState == 4 && this.status == 200) {
        // Typical action to be performed when the document is ready:
            var data = JSON.parse(this.responseText)
            document.getElementById("events").innerHTML = ""
            for (i in data) {
                document.getElementById('events').innerHTML += 
                `<div class="col-12 card" style="
                margin-left: 0px!important;
                background: #ed213a; /* fallback for old browsers */
                background: linear-gradient(to right, #ec3750, #e9485e); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */">
                    <div class="card-container" style="text-align: left;">
                        <h4><b>${data[i]["Date"]}, ${data[i]["Time"]} EDT</b></h4>
                        <p>${data[i]["Action"]}</p>
                    </div>
                </div>`
            }
        }
    };
    xhttp.open("GET", "https://google-sheet-to-json.vercel.app/api", true);
    xhttp.send();
    document.getElementById("events").innerHTML = "Loading events..."
    } catch (err) {
        document.getElementById("events").innerHTML = `Uh oh! We weren't able to get events. ${err}`
    }
</script>
