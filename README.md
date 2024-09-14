// Function to get data from local storage or initialize empty data
function getData() {
  const storedData = JSON.parse(localStorage.getItem('healthData'));
  return storedData || {
    weight: [],
    caloriesBurned: [],
    caloriesConsumed: []
  };
}

// Function to save data to local storage
function saveData(data) {
  localStorage.setItem('healthData', JSON.stringify(data));
}

// Get data from local storage
let healthData = getData();

// Function to add a new entry
function addEntry(type, value) {
  healthData[type].push({ date: new Date().toLocaleDateString(), value });
  saveData(healthData);
  console.log(New ${type} entry added: ${value} on ${new Date().toLocaleDateString()});
}

// Function to display all entries
function displayEntries(type) {
  console.log(n--- ${type} Entries ---);
  healthData[type].forEach(entry => {
    console.log(Date: ${entry.date}, Value: ${entry.value});
  });
}

// Example usage
addEntry('weight', 170); // Add weight entry
addEntry('caloriesBurned', 500); // Add calories burned entry
addEntry('caloriesConsumed', 2000); // Add calories consumed entry

// Display all entries
displayEntries('weight');
displayEntries('caloriesBurned');
displayEntries('caloriesConsumed');

   <!DOCTYPE html>
   <html lang="en">
   <head>
     <meta charset="UTF-8">
     <title>Health Tracker</title>
   </head>
   <body>
     <script src="health-tracker.js"></script>
   </body>
   </html>
