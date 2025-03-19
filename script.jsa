document.getElementById('flight-search-form').addEventListener('submit', function(event) {
    event.preventDefault();
    
    const origin = document.getElementById('origin').value;
    const destination = document.getElementById('destination').value;
    const departureDate = document.getElementById('departure-date').value;
    const resultsDiv = document.getElementById('results');

    resultsDiv.innerHTML = '検索中...';

    fetch(`https://freewebapi.com/api/flight?origin=${origin}&destination=${destination}&departure_date=${departureDate}`)
        .then(response => response.json())
        .then(data => {
            resultsDiv.innerHTML = '';
            if (data.flights && data.flights.length > 0) {
                data.flights.forEach(flight => {
                    const flightDiv = document.createElement('div');
                    flightDiv.className = 'flight';
                    flightDiv.innerHTML = `
                        <p><strong>航空会社:</strong> ${flight.airline}</p>
                        <p><strong>便名:</strong> ${flight.flight_number}</p>
                        <p><strong>出発時刻:</strong> ${flight.departure_time}</p>
                        <p><strong>到着時刻:</strong> ${flight.arrival_time}</p>
                    `;
                    resultsDiv.appendChild(flightDiv);
                });
            } else {
                resultsDiv.innerHTML = '便が見つかりませんでした。';
            }
        })
        .catch(error => {
            console.error('Error fetching flight data:', error);
            resultsDiv.innerHTML = 'エラーが発生しました。もう一度お試しください。';
        });
});
