<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Custom Calendar</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f4;
        }
        .calendar-container {
            width: 350px;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            text-align: center;
        }
        .calendar-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .calendar-header button {
            background: none;
            border: none;
            font-size: 20px;
            cursor: pointer;
        }
        .weekdays {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
            font-weight: bold;
            margin-top: 10px;
        }
        .calendar-days {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
            gap: 5px;
            margin-top: 10px;
        }
        .day {
            background: #e3e3e3;
            padding: 10px;
            border-radius: 5px;
            text-align: center;
            cursor: pointer;
        }
        .day:hover {
            background: #ccc;
        }
        .current-day {
            background: #ff6f61;
            color: white;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="calendar-container">
        <div class="calendar-header">
            <button id="prevMonth">&lt;</button>
            <h2 id="monthYear"></h2>
            <button id="nextMonth">&gt;</button>
        </div>
        <div class="calendar">
            <div class="weekdays">
                <div>Sun</div><div>Mon</div><div>Tue</div><div>Wed</div>
                <div>Thu</div><div>Fri</div><div>Sat</div>
            </div>
            <div class="calendar-days"></div>
        </div>
    </div>
    <script>
        const calendarDays = document.querySelector('.calendar-days');
        const monthYear = document.getElementById('monthYear');
        const prevMonthBtn = document.getElementById('prevMonth');
        const nextMonthBtn = document.getElementById('nextMonth');

        let date = new Date();
        let currentMonth = date.getMonth();
        let currentYear = date.getFullYear();

        const renderCalendar = () => {
            calendarDays.innerHTML = '';

            const firstDay = new Date(currentYear, currentMonth, 1).getDay();
            const lastDate = new Date(currentYear, currentMonth + 1, 0).getDate();

            monthYear.textContent = new Date(currentYear, currentMonth).toLocaleDateString('en-US', { month: 'long', year: 'numeric' });

            for (let i = 0; i < firstDay; i++) {
                calendarDays.innerHTML += `<div></div>`;
            }

            for (let i = 1; i <= lastDate; i++) {
                const dayDiv = document.createElement('div');
                dayDiv.classList.add('day');
                dayDiv.textContent = i;

                if (i === date.getDate() && currentMonth === date.getMonth() && currentYear === date.getFullYear()) {
                    dayDiv.classList.add('current-day');
                }

                calendarDays.appendChild(dayDiv);
            }
        };

        prevMonthBtn.addEventListener('click', () => {
            currentMonth--;
            if (currentMonth < 0) {
                currentMonth = 11;
                currentYear--;
            }
            renderCalendar();
        });

        nextMonthBtn.addEventListener('click', () => {
            currentMonth++;
            if (currentMonth > 11) {
                currentMonth = 0;
                currentYear++;
            }
            renderCalendar();
        });

        renderCalendar();
    </script>
</body>


<table border="1">
    <thead>
        <tr>
            <th>Header 1</th>
            <th>Header 2</th>
            <th>Header 3</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td> </td>
            <td> </td>
            <td> </td>
        </tr>
        <tr>
            <td> </td>
            <td> </td>
            <td> </td>
        </tr>
        <tr>
            <td> </td>
            <td> </td>
            <td> </td>
        </tr>
    </tbody>
</table>
