<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Food Web Site Finder</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f8f9fa;
            margin: 0;
            padding: 20px;
        }
        header {
            text-align: center;
            padding: 20px;
            background-color: #343a40;
            color: white;
        }
        h1 {
            margin: 0;
        }
        .search-bar {
            max-width: 600px;
            margin: 20px auto;
            display: flex;
            justify-content: center;
        }
        input[type="text"] {
            width: 80%;
            padding: 10px;
            border: 1px solid #ced4da;
            border-radius: 4px;
        }
        button {
            padding: 10px 20px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            margin-left: 10px;
        }
        button:hover {
            background-color: #218838;
        }
        .app-link {
            display: block;
            text-align: center;
            margin: 20px auto;
        }
        .app-link a {
            padding: 10px 20px;
            background-color: #007bff;
            color: white;
            text-decoration: none;
            border-radius: 4px;
        }
        .app-link a:hover {
            background-color: #0056b3;
        }
        .results {
            max-width: 800px;
            margin: 20px auto;
        }
        .result-item {
            background-color: white;
            padding: 20px;
            margin-bottom: 10px;
            border-radius: 4px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            display: flex;
            align-items: flex-start;
        }
        .result-item img {
            width: 100px;
            height: 100px;
            border-radius: 4px;
            margin-right: 20px;
        }
        .result-item iframe, .result-item video {
            width: 100%;
            height: 200px;
            border-radius: 4px;
            margin-top: 10px;
        }
        .result-item h3 {
            margin-top: 0;
            margin-bottom: 5px;
        }
    </style>
</head>
<body>

<header>
    <h1>Food Web Site Finder</h1>
</header>

<div class="search-bar">
    <input type="text" id="searchInput" placeholder="Search for a food website...">
    <button onclick="searchSites()">Search</button>
</div>

<div class="app-link">
    <a href="https://trustedmall.com" target="_blank">Visit Trusted Mall</a>
</div>

<div class="results" id="resultsContainer">
    <!-- Search results will be displayed here -->
</div>

<script>
    function searchSites() {
        const query = document.getElementById('searchInput').value;
        const resultsContainer = document.getElementById('resultsContainer');
        
        // Clear previous results
        resultsContainer.innerHTML = '';

        // Simulated search results with images and various video sources
        const dummyResults = [
            { 
                name: "Tasty Recipes", 
                url: "https://tasty.co", 
                img: "https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.shutterstock.com%2Fsearch%2Findian-recipe&psig=AOvVaw27S3gAD4ib7ltZT8cv5fkZ&ust=1726661133530000&source=images&cd=vfe&opi=89978449&ved=0CBEQjRxqFwoTCKiWnJT4yYgDFQAAAAAdAAAAABAE", 
                video: "https://youtube.com/shorts/OKiA4DUpauA?si=Jz83NGxO3D9g6QyQ" 
            },
            { 
                name: "Allrecipes", 
                url: "https://allrecipes.com", 
                img: "https://via.placeholder.com/100?text=Allrecipes", 
                video: "https://player.vimeo.com/video/76979871" 
            },
            { 
                name: "Epicurious", 
                url: "https://epicurious.com", 
                img: "https://via.placeholder.com/100?text=Epicurious", 
                video: "https://www.instagram.com/p/CVX8sxlFZqf/embed"
            },
            { 
                name: "Serious Eats", 
                url: "https://seriouseats.com", 
                img: "https://via.placeholder.com/100?text=Serious+Eats", 
                video: "https://www.instagram.com/p/CVX8sxlFZqf/embed"
            },
            { 
                name: "Food Network", 
                url: "https://foodnetwork.com", 
                img: "https://via.placeholder.com/100?text=Food+Network", 
                video: "https://www.youtube.com/embed/1APZ0-efg_A" 
            }
        ];

        // Filter dummy results by query
        const filteredResults = dummyResults.filter(result => 
            result.name.toLowerCase().includes(query.toLowerCase())
        );

        // Display results with images and videos
        filteredResults.forEach(result => {
            const resultItem = document.createElement('div');
            resultItem.classList.add('result-item');

            // Handle video content (including Instagram embeds)
            let videoContent = '';
            if (result.video.includes('instagram.com')) {
                videoContent = `<iframe src="${result.video}" frameborder="0" allowfullscreen scrolling="no"></iframe>`;
            } else {
                videoContent = `<iframe src="${result.video}" frameborder="0" allowfullscreen></iframe>`;
            }

            resultItem.innerHTML = `
                <img src="${result.img}" alt="${result.name}">
                <div>
                    <h3>${result.name}</h3>
                    <a href="${result.url}" target="_blank">${result.url}</a>
                    ${videoContent}
                </div>
            `;
            resultsContainer.appendChild(resultItem);
        });

        // If no results
        if (filteredResults.length === 0) {
            resultsContainer.innerHTML = '<p>No results found.</p>';
        }
    }
</script>

</body>
</html>
