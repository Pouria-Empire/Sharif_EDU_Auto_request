____ Pouria 007___

Just login to my.edu.sharif.edu

press f12

paste the following script:

const jsonObject = JSON.parse(localStorage.getItem('persist:root'));
const baseUrl = 'https://my.edu.sharif.edu/api/reg';
const authorizationToken = jsonObject['token']

// Define an array of course data
const courses = [
    { action: 'add', course: '40453-1', units: 3 },
    { action: 'add', course: '12345-2', units: 3 },
    { action: 'add', course: '67890-3', units: 3 }
];


// Function to send a single POST request for a course
function sendPostRequest(courseData) {
    const url = `${baseUrl}`;
    
    // Send the POST request and return the promise
    return fetch(url, {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
            'Authorization': JSON.parse(authorizationToken)
        },
        body: JSON.stringify(courseData)
    })
    .then(response => response.json());
}

// Function to send all POST requests after a delay
function sendAllRequests() {
    console.log("Sending all requests after 5 seconds...");
    
    // Use Promise.all to send all requests concurrently
    Promise.all(courses.map(courseData => sendPostRequest(courseData)))
    .then(responses => {
        responses.forEach((response, index) => {
            console.log(`Response for Course ${index + 1}:`, response);
        });
    })
    .catch(error => console.error('Error:', error.message));
}

// Schedule sending all requests after a 5-second delay
setTimeout(sendAllRequests, 5000); // Delay for 5 seconds (5000 milliseconds)








Paste your course id
Paste Group id
Paste units


Have Fun!


