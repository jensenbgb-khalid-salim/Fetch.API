# Fetch.API
MY-Fetch
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Flickr</title>
</head>

<body>

    <style>
        .container {
            position: relative;
            position: absolute;
            top: 50px;
            display: flex;
            justify-content: center;
        }
        
        #search {
            padding: 10px;
            font-size: 25px;
            border: 1px solid grey;
            float: left;
            width: 70%;
            background: #f1f1f1;
        }
        
        #submit {
            float: left;
            width: 25%;
            padding: 10px;
            background: rgb(245, 162, 7);
            color: black;
            font-size: 25px;
            border: 1px solid grey;
            border-left: none;
            cursor: pointer;
        }
        
        #submit:hover {
            background: #ff8800;
        }
        
        #search::after {
            content: "";
            clear: both;
            display: table;
        }
        
        #outputDiv {
            display: grid;
            grid-template-columns: repeat(6, 1fr);
            grid-gap: 5px;
            grid-auto-rows: repeat(6, 1fr);
            position: absolute;
            top: 250px;
        }
        
        .cover {
            display: flex;
            justify-content: center;
            background-color: rgb(255, 115, 0);
            height: 200px;
        }
    </style>

    <section class="cover">
        <div class="container">
            <input id="search" type="text" placeholder="search text" />
            <button id="submit" onclick="Fetch()">Submit</button>
        </div>

    </section>

    <div id="outputDiv"></div>

    <script>
        function Fetch() {
            var script = document.createElement('script');
            script.src = "https://api.flickr.com/services/feeds/photos_public.gne?format=json&tags=" + document.getElementById("search").value;;
            document.querySelector('head').appendChild(script);
        }

        function jsonFlickrFeed(data) {
            var image = "";
            data.items.forEach(function(element) {
                image += "<img src=\"" + element.media.m + "\"/>";
            });
            document.getElementById("outputDiv").innerHTML = image;
        }
    </script>
</body>

</html>
