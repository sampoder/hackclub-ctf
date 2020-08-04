---
title: Timeline
layout: default
---

Here's a schedule of events! Times are in EST unless otherwise noted.

<p id="msg"><p>

<div class="row section">
<div id="events"></div></div>


    
<script>
    try {
    var xhttp = new XMLHttpRequest();
    xhttp.onreadystatechange = function() {
        if (this.readyState == 4 && this.status == 200) {
        // Typical action to be performed when the document is ready:
            var data = JSON.parse(this.responseText)
            document.getElementById("msg").innerHTML = ""
            for (i in data) {
                document.getElementById('events').innerHTML += 
                `<div class="col-12 card" style="
                background: #ed213a; /* fallback for old browsers */
                background: linear-gradient(to right, #ec3750, #e9485e); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */">
                    <div class="card-container" style="text-align: left;">
                        <h4><b>${data[i]["Date"]}, ${data[i]["Time"]} EST</b></h4>
                        <p>${data[i]["Action"]}</p>
                    </div>
                </div>`
            }
        }
    };
    xhttp.open("GET", "https://google-sheet-to-json.vercel.app/api", true);
    xhttp.send();
    document.getElementById("msg").innerHTML = "Loading events..."
    } catch (err) {
        document.getElementById("msg").innerHTML = `Uh oh! We weren't able to get events. ${err}`
    }
</script>