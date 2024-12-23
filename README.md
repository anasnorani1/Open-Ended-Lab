# Open-Ended-Lab
#The ICT Open Ended Lab Allows us to make a webpage of different landmarks of our choice
#The Code is given by :
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GIS Landmark DataBase</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #eef2f3;
            color: #333;
        }
        header {
            background: linear-gradient(90deg, #bbd0ff, #b8c0ff);
            color: rgb(26, 22, 22);
            padding: 2rem 1rem;
            text-align: center;
            font-size: 1.5rem;
            font-weight: bold;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
        }
        .info-section {
    background: #b8c0ff;
    padding: 2rem;
    margin: 2rem auto;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    max-width: 800px;
    text-align: left;
    color: #333;
}

.info-section h3 {
    font-size: 1.8rem;
    color: #03045e;
    margin-bottom: 1rem;
    text-decoration: underline;
}

.info-section p {
    font-size: 1rem;
    line-height: 1.6;
    margin: 0.5rem 0;
}

.info-section a {
    color: #03045e;
    font-weight: bold;
    text-decoration: none;
}

.info-section a:hover {
    text-decoration: underline;
    color: #03045e;
}

        .container {
            max-width: 1000px;
            margin: 3rem auto;
            padding: 2rem;
            background: white;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }
        .landmark {
            margin-bottom: 2.5rem;
            padding: 1.5rem;
            border: 1px solid #ddd;
            border-radius: 8px;
            transition: transform 0.2s ease, box-shadow 0.2s ease;
            cursor: pointer;
        }
        .landmark:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.1);
        }
        .landmark img {
            width: 100%;
            height: auto;
            border-radius: 8px;
            margin-bottom: 1rem;
        }
        .landmark h2 {
            margin: 0.5rem 0;
            font-size: 1.8rem;
            color: #03045e;
        }
        .coordinates {
            font-style: italic;
            color: #555;
            margin-bottom: 1rem;
        }
        .landmark p {
            line-height: 1.6;
            color: #444;
        }
        footer {
            text-align: center;
            padding: 1rem;
            background: #bbd0ff;
            color: rgb(32, 26, 26);
            font-size: 0.9rem;
            margin-top: 3rem;
        }
        .search-container {
            text-align: center;
            margin-bottom: 2rem;
        }
        .search-container input {
            padding: 0.5rem;
            font-size: 1rem;
            width: 80%;
            max-width: 300px;
            margin-bottom: 1rem;
            border: 1px solid #f1f1f1;
            border-radius: 4px;
        }
        #map {
            height: 400px;
            margin-top: 2rem;
            border-radius: 8px;
            background-color: #f1f1f1;
        }
        .popup-description {
            font-size: 1rem;
            color: #333;
        }
        .insights {
            margin-top: 2rem;
            background-color: #f9f9f9;
            padding: 1.5rem;
            border-radius: 8px;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
        }
        .insights h3 {
            font-size: 1.6rem;
            color: #03045e;
        }
        .comparative-analysis {
            margin-top: 2rem;
            background-color: #f9f9f9;
            padding: 1.5rem;
            border-radius: 8px;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 1rem;
        }
        table, th, td {
            border: 1px solid #ddd;
        }
        th, td {
            padding: 12px;
            text-align: left;
        }
        th {
            background-color: #f2f2f2;
            color: #03045e;
        }
    </style>
    <link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />
    <link rel="stylesheet" href="https://unpkg.com/leaflet.markercluster/dist/MarkerCluster.css" />
    <link rel="stylesheet" href="https://unpkg.com/leaflet.markercluster/dist/MarkerCluster.Default.css" />
</head>
<body>
    <header>
        <h1>Landmark Information Database</h1>
    </header>

    <!-- Search Bar -->
    <div class="search-container">
        <input type="text" id="search" placeholder="Search for a landmark..." oninput="searchLandmarks()">
    </div>

    <div class="container" id="landmark-container">
        <!-- Landmarks will be dynamically inserted here -->
    </div>

    <!-- Insights Section -->
    <div class="insights">
        <h3>Special Insights</h3>
        <p><strong>Faisal Mosque:</strong> The mosque's unique tent-like structure is designed to resemble a Bedouin desert tent, which is unlike traditional mosque architecture.</p>
        <p><strong>Badshahi Mosque:</strong> Known as one of the largest mosques in the world, its Mughal architecture sets it apart, with intricately detailed frescoes and extensive courtyards.</p>
        <p><strong>Deosai National Park:</strong> The high-altitude plateau features unique wildlife, including the endangered Himalayan brown bear. Its rolling meadows are among the highest in the world.</p>
    </div>

    <!-- Comparative Analysis Section -->
    <div class="comparative-analysis">
        <h3>Comparative Analysis of Landmarks</h3>
        <table>
            <thead>
                <tr>
                    <th>Landmark</th>
                    <th>Region</th>
                    <th>Architectural Style</th>
                    <th>Historical Significance</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>Faisal Mosque</td>
                    <td>Islamabad</td>
                    <td>Modern Islamic Architecture</td>
                    <td>Symbol of modern Islamic architecture in Pakistan</td>
                </tr>
                <tr>
                    <td>Badshahi Mosque</td>
                    <td>Lahore</td>
                    <td>Mughal Architecture</td>
                    <td>One of the largest mosques in the world, a significant Mughal architectural marvel</td>
                </tr>
                <tr>
                    <td>Mohenjo-Daro</td>
                    <td>Sindh</td>
                    <td>Indus Valley Civilization</td>
                    <td>An ancient city showcasing the advancements of the Indus Valley Civilization</td>
                </tr>
                <tr>
                    <td>Hunza Valley</td>
                    <td>Gilgit-Baltistan</td>
                    <td>Natural Beauty</td>
                    <td>Known for its breathtaking scenery and historical forts like Baltit and Altit</td>
                </tr>
                <tr>
                    <td>Deosai National Park</td>
                    <td>Gilgit-Baltistan</td>
                    <td>Natural Beauty</td>
                    <td>A unique high-altitude plateau with endangered wildlife</td>
                </tr>
            </tbody>
        </table>
    </div>

    <div id="map"></div>

    <footer>
        <div>
            <h3>About Us</h3>
            <p>
                The Landmark Information Database is a platform dedicated to showcasing the rich heritage, stunning natural beauty, and architectural marvels of Pakistan.
                Our mission is to provide detailed and accurate information to both travelers and history enthusiasts.
            </p>
        </div>
        <div>
            <h3>Contact Us</h3>
            <p>
                <strong>Email:</strong> <a href = "mailto:anorani.bsds24seecs@seecs.edu.pk">anorani.bsds24seecs@seecs.edu.pk</a><br>
                <strong>Phone:</strong> +92-370-8068311<br>
                <strong>LinkedIn Profile:</strong> <a href = "https://www.linkedin.com/in/anasnorani1/" target="blank">Anas Norani</a><br>
                <strong>Address:</strong> National University of Science & Technology (NUST), H-12 Islamabad, Pakistan
            </p>
        </div>
        <div>
            <h3>&copy; 2024 Landmarks of Pakistan | All rights reserved.<br>Developed By Anas Norani</h3>
        </div>
    </footer>
    <script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>
    <script src="https://unpkg.com/leaflet.markercluster/dist/leaflet.markercluster.js"></script>
    <script>
        // Array to store all landmarks with their details and images in different formats
        const landmarks = [
            {
                name: "Faisal Mosque",
                lat: 33.7294,
                lng: 73.0379,
                description: "An iconic mosque and a symbol of modern Islamic architecture. Known for its tent-like design and scenic backdrop of the Margalla Hills.",
                images: {
                    jpg: "https://res.cloudinary.com/www-travelpakistani-com/image/upload/v1661243930/Faisal_Mosque_travelpakistani.jpg"
                }
            },
            {
                name: "Badshahi Mosque",
                lat: 31.5889,
                lng: 74.3106,
                description: "A Mughal-era mosque known for its grand architecture, vast courtyards, and intricate frescoes.",
                images: {
                    jpg: "https://images.pexels.com/photos/12912453/pexels-photo-12912453.jpeg"
                }
            },
            {
                name: "Mohenjo-Daro",
                lat: 27.3274,
                lng: 68.1385,
                description: "Ancient ruins of the Indus Valley Civilization, featuring planned streets, advanced drainage systems, and historical significance.",
                images: {
                    jpg: "https://i.dawn.com/primary/2022/12/301129449abf47b.jpg"
                }
            },
            {
                name: "Hunza Valley",
                lat: 35.3265,
                lng: 74.7625,
                description: "A beautiful mountainous valley known for its breathtaking views and historical forts.",
                images: {
                    jpg: "https://i.pinimg.com/736x/4d/9d/27/4d9d27992f06ba124e6854fa528334e9.jpg"
                }
            },
            {
                name: "Deosai National Park",
                lat: 35.3030,
                lng: 75.1665,
                description: "A high-altitude plateau, home to rare wildlife such as the Himalayan brown bear.",
                images: {
                    jpg: "https://i.pinimg.com/736x/b6/44/19/b644194b2550a0c47d5a9faf8876b390.jpg"
                }
            }
        ];

        // Function to fetch weather data
        async function fetchWeather(lat, lng) {
            const apiKey = '7b8f39d9493b04045ef00a282a7c9309';  //  OpenWeatherMap API key
            const url = `https://api.openweathermap.org/data/2.5/weather?lat=${lat}&lon=${lng}&units=metric&appid=${apiKey}`;

            try {
                const response = await fetch(url);
                const data = await response.json();
                const weather = data.weather[0].description;
                const temp = data.main.temp;
                return `Weather: ${weather}, Temp: ${temp}°C`;
            } catch (error) {
                console.error("Error fetching weather data:", error);
                return "Weather data unavailable";
            }
        }

        // Populate the landmark container with each landmark
        const landmarkContainer = document.getElementById('landmark-container');
        landmarks.forEach(async (landmark) => {
            let weatherInfo = await fetchWeather(landmark.lat, landmark.lng);
            let div = document.createElement('div');
            div.className = 'landmark';
            div.innerHTML = `
                <img src="${landmark.images.jpg}" alt="${landmark.name}">
                <h2>${landmark.name}</h2>
                <p class="coordinates">Latitude: ${landmark.lat}° N, Longitude: ${landmark.lng}° E</p>
                <p>${landmark.description}</p>
                <p><strong>${weatherInfo}</strong></p>
            `;
            landmarkContainer.appendChild(div);
        });

        // Search functionality
        function searchLandmarks() {
    const searchQuery = document.getElementById('search').value.toLowerCase().trim();
    
    // Clear the landmark container to avoid duplicates
    landmarkContainer.innerHTML = '';

    // If the search query is empty, show all landmarks
    if (searchQuery === '') {
        renderLandmarks(landmarks);
        return;
    }

    // Filter landmarks to match the search query anywhere in the name (case insensitive)
    const filteredLandmarks = landmarks.filter(landmark =>
        landmark.name.toLowerCase().includes(searchQuery)
    );

    // Display filtered results
    renderLandmarks(filteredLandmarks);
}

function renderLandmarks(landmarksToRender) {
    landmarksToRender.forEach(async (landmark) => {
        let weatherInfo = await fetchWeather(landmark.lat, landmark.lng);
        let div = document.createElement('div');
        div.className = 'landmark';
        div.innerHTML = `
            <img src="${landmark.images.jpg}" alt="${landmark.name}">
            <h2>${landmark.name}</h2>
            <p class="coordinates">Latitude: ${landmark.lat}° N, Longitude: ${landmark.lng}° E</p>
            <p>${landmark.description}</p>
            <p><strong>${weatherInfo}</strong></p>
        `;
        landmarkContainer.appendChild(div);
    });
}


        // Initialize the map
        const map = L.map('map').setView([33.6844, 73.0479], 5);

        // Add tile layer to the map
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
        }).addTo(map);

        // Add markers for each landmark
        landmarks.forEach(landmark => {
            L.marker([landmark.lat, landmark.lng])
                .addTo(map)
                .bindPopup(`<strong>${landmark.name}</strong><br><img src="${landmark.images.jpg}" alt="${landmark.name}" width="150px"><p class="popup-description">${landmark.description}</p>`);
        });
    </script>
</body>
</html>

