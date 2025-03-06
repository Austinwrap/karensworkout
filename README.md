<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Karen's Lil' Laundry Lift</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(to bottom, #fff0f5, #f0f8ff);
            color: #444;
            overflow-x: hidden;
            line-height: 1.4;
        }
        .welcome-page {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            background: linear-gradient(135deg, #ffb6c1, #ffccd5, #ffe4e1);
            text-align: center;
            padding: 15px;
            color: #fff;
            text-shadow: 1px 1px 2px rgba(255, 105, 180, 0.3);
            animation: sparkle 1.5s infinite alternate;
        }
        @keyframes sparkle {
            0% { box-shadow: 0 0 8px rgba(255, 182, 193, 0.6); }
            100% { box-shadow: 0 0 15px rgba(255, 228, 225, 0.6); }
        }
        .welcome-page h1 {
            font-size: 2.5em;
            margin: 10px 0;
            font-weight: bold;
            letter-spacing: 1px;
        }
        .welcome-page p {
            font-size: 1.4em;
            margin: 6px 0;
            font-style: italic;
        }
        .enter-btn {
            padding: 10px 25px;
            font-size: 1.1em;
            background: #fff;
            border: 2px solid #ff69b4;
            border-radius: 25px;
            color: #ff69b4;
            cursor: pointer;
            transition: all 0.3s;
            margin-top: 15px;
        }
        .enter-btn:hover {
            background: #ff69b4;
            color: #fff;
            transform: scale(1.05);
        }
        .main-content {
            display: none;
            padding: 10px;
            text-align: center;
            background: linear-gradient(to bottom, #f0f8ff, #fff0f5);
            min-height: 100vh;
            color: #444;
        }
        .day-buttons {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 8px;
            margin: 10px auto;
            max-width: 300px;
        }
        .day-btn {
            padding: 8px 15px;
            background: #ffd1dc;
            border: 1px solid #ff99cc;
            border-radius: 15px;
            color: #ff69b4;
            cursor: pointer;
            font-size: 0.9em;
            transition: all 0.3s;
        }
        .day-btn:hover {
            background: #ff99cc;
            color: #fff;
        }
        .all-btn {
            padding: 6px 12px;
            background: #ffccd5;
            border: 1px solid #ff69b4;
            border-radius: 20px;
            color: #ff69b4;
            cursor: pointer;
            font-size: 0.8em;
            margin: 10px 0;
            transition: all 0.3s;
        }
        .all-btn:hover {
            background: #ff69b4;
            color: #fff;
        }
        .workout-popup {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: linear-gradient(135deg, #fff0f5, #f0f8ff);
            padding: 15px;
            border-radius: 20px;
            box-shadow: 0 0 12px rgba(255, 105, 180, 0.3);
            max-width: 85%;
            max-height: 75vh;
            overflow-y: auto;
            z-index: 10;
            border: 2px dashed #ff99cc;
        }
        .close-btn, .nav-btn, .skip-btn {
            font-size: 1.3em;
            cursor: pointer;
            color: #ff69b4;
            padding: 5px;
            border: none;
            background: none;
            transition: color 0.3s;
        }
        .close-btn {
            position: absolute;
            top: 8px;
            right: 8px;
        }
        .nav-btn:hover, .close-btn:hover, .skip-btn:hover {
            color: #ffb6c1;
        }
        .motivate-btn {
            padding: 8px 15px;
            background: #ffd1dc;
            border: 1px solid #ff99cc;
            border-radius: 15px;
            color: #ff69b4;
            font-size: 0.9em;
            cursor: pointer;
            margin: 10px 0;
            transition: all 0.3s;
        }
        .motivate-btn:hover {
            background: #ff99cc;
            color: #fff;
        }
        h2 {
            color: #ff69b4;
            font-size: 1.5em;
            margin-bottom: 8px;
            font-weight: bold;
        }
        h3 {
            color: #ff99cc;
            font-size: 1.2em;
            margin: 8px 0;
        }
        ul {
            list-style-type: heart;
            padding-left: 20px;
            text-align: left;
            font-size: 0.9em;
            color: #555;
        }
        li {
            margin-bottom: 5px;
        }
        p {
            font-size: 0.9em;
            margin: 8px 0;
            color: #666;
        }
        .nav-container {
            display: flex;
            justify-content: space-between;
            margin-top: 10px;
        }
        .reminder {
            font-style: italic;
            color: #ff99cc;
            font-size: 0.85em;
        }
        @media (max-width: 600px) {
            .welcome-page h1 { font-size: 2em; }
            .welcome-page p { font-size: 1.2em; }
            .day-btn { font-size: 0.85em; }
            .workout-popup { padding: 12px; }
        }
    </style>
</head>
<body>
    <div class="welcome-page" id="welcome">
        <h1>¡Hiii, Karen!</h1>
        <p></p>
        <p></p>
        <p></p>
        <button class="enter-btn" onclick="enterSite()">¡Let’s Go!</button>
    </div>

    <div class="main-content" id="main">
        <h2>Karen’s Cute Dumbbell Days</h2>
        <p class="reminder">Psst: Bump up weights every 2-3 weeks, cutie!</p>
        <div class="day-buttons">
            <button class="day-btn" onclick="showWorkout('Monday')">Monday</button>
            <button class="day-btn" onclick="showWorkout('Tuesday')">Tuesday</button>
            <button class="day-btn" onclick="showWorkout('Wednesday')">Wednesday</button>
            <button class="day-btn" onclick="showWorkout('Thursday')">Thursday</button>
            <button class="day-btn" onclick="showWorkout('Friday')">Friday</button>
            <button class="day-btn" onclick="showWorkout('Saturday')">Saturday</button>
            <button class="day-btn" onclick="showWorkout('Sunday')">Sunday</button>
        </div>
        <button class="motivate-btn" onclick="showMotivation()">¡Gimme a Boost!</button>
        <button class="all-btn" onclick="showAllWorkouts(0)">All Workouts</button>
    </div>

    <!-- Week 1-4 Workouts -->
    <div class="workout-popup" id="Monday">
        <span class="close-btn" onclick="closePopup('Monday')">X</span>
        <h2>Monday: Chest & Triceps (Week 1)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Jumping Jacks: 3x30 sec</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>Closed Grip DB Press: 22.5 lbs, 3x12</li>
            <li>DB Floor Press: 22.5 lbs, 3x11</li>
            <li>Overhead DB Tricep Ext: 22.5 lbs, 3x10</li>
            <li>DB Skull Crushers: 12.5 lbs, 3x10</li>
            <li>DB Chest Flys: 12.5 lbs, 3x12</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="showWorkout('Sunday')">◄ Back</button>
            <button class="skip-btn" onclick="skipWorkout('Monday')">Skip</button>
            <button class="nav-btn" onclick="showWorkout('Tuesday')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Tuesday">
        <span class="close-btn" onclick="closePopup('Tuesday')">X</span>
        <h2>Tuesday: Back & Biceps (Week 1)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Arm Swings: 2x20</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Bent Over Rows: 22.5 lbs, 3x12</li>
            <li>DB Single Arm Row: 22.5 lbs, 3x12</li>
            <li>DB Hammer Curls: 12.5 lbs, 3x10</li>
            <li>DB Alternating Curls: 12.5 lbs, 3x8</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="showWorkout('Monday')">◄ Back</button>
            <button class="skip-btn" onclick="skipWorkout('Tuesday')">Skip</button>
            <button class="nav-btn" onclick="showWorkout('Wednesday')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Wednesday">
        <span class="close-btn" onclick="closePopup('Wednesday')">X</span>
        <h2>Wednesday: Legs Day 1 (Week 1)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>High Knees: 3x30 sec</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Elevated Squats: 20 lbs, 3x10</li>
            <li>DB RDLs: 15 lbs each, 3x10</li>
            <li>DB Sumo Squats: 25 lbs, 3x12</li>
            <li>DB Good Mornings: 30 lbs, 3x10</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="showWorkout('Tuesday')">◄ Back</button>
            <button class="skip-btn" onclick="skipWorkout('Wednesday')">Skip</button>
            <button class="nav-btn" onclick="showWorkout('Thursday')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Thursday">
        <span class="close-btn" onclick="closePopup('Thursday')">X</span>
        <h2>Thursday: Shoulders (Week 1)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Shoulder Rolls: 2x15</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Front Raises: 8 lbs, 3x12</li>
            <li>DB Arnold Press: 12 lbs, 3x10</li>
            <li>DB Lateral Raises: 8 lbs, 3x10</li>
            <li>DB Upright Rows: 12 lbs, 3x12</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="showWorkout('Wednesday')">◄ Back</button>
            <button class="skip-btn" onclick="skipWorkout('Thursday')">Skip</button>
            <button class="nav-btn" onclick="showWorkout('Friday')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Friday">
        <span class="close-btn" onclick="closePopup('Friday')">X</span>
        <h2>Friday: Legs Day 2 (Week 1)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Walking Lunges: 2x10</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Glute Bridge: 25 lbs, 3x12</li>
            <li>DB RDLs: 25 lbs, 3x12</li>
            <li>DB Step-Ups: 15 lbs each, 3x10</li>
            <li>DB Goblet Squats: 20 lbs, 3x12</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="showWorkout('Thursday')">◄ Back</button>
            <button class="skip-btn" onclick="skipWorkout('Friday')">Skip</button>
            <button class="nav-btn" onclick="showWorkout('Saturday')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Saturday">
        <span class="close-btn" onclick="closePopup('Saturday')">X</span>
        <h2>Saturday: Full Body (Week 1)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Jump Rope (or mimic): 3x1 min</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Chest Press: 22.5 lbs, 3x12</li>
            <li>DB Bent Over Rows: 22.5 lbs, 3x12</li>
            <li>DB Squats: 20 lbs, 3x10</li>
            <li>DB Shoulder Press: 12 lbs, 3x10</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="showWorkout('Friday')">◄ Back</button>
            <button class="skip-btn" onclick="skipWorkout('Saturday')">Skip</button>
            <button class="nav-btn" onclick="showWorkout('Sunday')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Sunday">
        <span class="close-btn" onclick="closePopup('Sunday')">X</span>
        <h2>Sunday: Core & Recovery (Week 1)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Plank Hold: 3x30 sec</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Chest Flys: 12.5 lbs, 3x12</li>
            <li>DB Single Arm Row: 22.5 lbs, 3x12</li>
            <li>DB Russian Twists: 10 lbs, 3x15</li>
            <li>DB Deadlifts: 25 lbs, 3x10</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="showWorkout('Saturday')">◄ Back</button>
            <button class="skip-btn" onclick="skipWorkout('Sunday')">Skip</button>
            <button class="nav-btn" onclick="showWorkout('Monday')">Next ►</button>
        </div>
    </div>

    <!-- Alternate Workouts -->
    <div class="workout-popup" id="Alt1">
        <span class="close-btn" onclick="closePopup('Alt1')">X</span>
        <h2>Chest & Triceps (Week 2)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Arm Circles: 2x20</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Bench Press: 25 lbs, 4x10</li>
            <li>DB Tricep Kickbacks: 12.5 lbs, 4x12</li>
            <li>DB Flys: 15 lbs, 4x10</li>
            <li>DB Overhead Press: 20 lbs, 4x8</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt1')">Back</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt2">
        <span class="close-btn" onclick="closePopup('Alt2')">X</span>
        <h2>Back & Biceps (Week 2)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Dead Hangs: 3x20 sec</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Reverse Flys: 10 lbs, 4x12</li>
            <li>DB Concentration Curls: 15 lbs, 4x10</li>
            <li>DB Underhand Rows: 25 lbs, 4x10</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt2')">Back</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt3">
        <span class="close-btn" onclick="closePopup('Alt3')">X</span>
        <h2>Legs (Week 2)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Leg Swings: 2x15</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Lunges: 20 lbs, 4x10</li>
            <li>DB Deadlifts: 30 lbs, 4x10</li>
            <li>DB Side Squats: 20 lbs, 4x12</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt3')">Back</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt4">
        <span class="close-btn" onclick="closePopup('Alt4')">X</span>
        <h2>Shoulders (Week 2)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Arm Swings: 2x20</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Rear Delt Flys: 10 lbs, 4x12</li>
            <li>DB Shoulder Press: 15 lbs, 4x10</li>
            <li>DB Lateral Raises: 10 lbs, 4x12</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt4')">Back</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt5">
        <span class="close-btn" onclick="closePopup('Alt5')">X</span>
        <h2>Legs (Week 3)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Butt Kicks: 3x30 sec</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Bulgarian Split Squats: 20 lbs, 4x10</li>
            <li>DB Glute Bridge: 30 lbs, 4x12</li>
            <li>DB Sumo Deadlifts: 25 lbs, 4x10</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt5')">Back</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt6">
        <span class="close-btn" onclick="closePopup('Alt6')">X</span>
        <h2>Full Body (Week 3)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Dynamic Stretch: 2 min</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Thrusters: 20 lbs, 4x10</li>
            <li>DB Renegade Rows: 15 lbs, 4x12</li>
            <li>DB Goblet Squats: 25 lbs, 4x10</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt6')">Back</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt7">
        <span class="close-btn" onclick="closePopup('Alt7')">X</span>
        <h2>Core (Week 3)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Plank Hold: 3x30 sec</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Side Bends: 15 lbs, 4x15</li>
            <li>DB Russian Twists: 12 lbs, 4x15</li>
            <li>DB Leg Raises: 10 lbs, 4x12</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt7')">Back</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt8">
        <span class="close-btn" onclick="closePopup('Alt8')">X</span>
        <h2>Chest & Triceps (Week 4)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Jumping Jacks: 3x30 sec</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Incline Press: 25 lbs, 4x10</li>
            <li>DB Tricep Overhead: 15 lbs, 4x12</li>
            <li>DB Flys: 15 lbs, 4x12</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt8')">Back</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt9">
        <span class="close-btn" onclick="closePopup('Alt9')">X</span>
        <h2>Back & Biceps (Week 4)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Arm Swings: 2x20</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Reverse Grip Rows: 25 lbs, 4x10</li>
            <li>DB Bicep Curls: 15 lbs, 4x12</li>
            <li>DB Single Arm Pulls: 20 lbs, 4x12</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt9')">Back</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt10">
        <span class="close-btn" onclick="closePopup('Alt10')">X</span>
        <h2>Full Body (Week 4)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>High Knees: 3x30 sec</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Clean & Press: 20 lbs, 4x10</li>
            <li>DB Deadlift to Row: 25 lbs, 4x10</li>
            <li>DB Squat to Curl: 15 lbs, 4x12</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt10')">Back</button>
        </div>
    </div>

    <!-- All Workouts Popup -->
    <div class="workout-popup" id="all-workouts">
        <span class="close-btn" onclick="closePopup('all-workouts')">X</span>
        <h2>Your Lil’ Workout List</h2>
        <div id="all-workout-content"></div>
        <div class="nav-container">
            <button class="nav-btn" onclick="showAllWorkouts(currentAllIndex - 1)">◄ Prev</button>
            <button class="nav-btn" onclick="showAllWorkouts(currentAllIndex + 1)">Next ►</button>
        </div>
    </div>

    <!-- Motivation Popup -->
    <div class="workout-popup" id="motivate">
        <span class="close-btn" onclick="closePopup('motivate')">X</span>
        <h2>¡Your Daily Sparkle!</h2>
        <p id="quote"></p>
    </div>

    <script>
        function enterSite() {
            document.getElementById('welcome').style.display = 'none';
            document.getElementById('main').style.display = 'block';
        }

        function showWorkout(day) {
            closeAllPopups();
            document.getElementById(day).style.display = 'block';
        }

        function closePopup(id) {
            document.getElementById(id).style.display = 'none';
        }

        function closeAllPopups() {
            document.querySelectorAll('.workout-popup').forEach(popup => {
                popup.style.display = 'none';
            });
        }

        const workoutProgression = {
            'Monday': ['Monday', 'Alt1', 'Alt8', 'Alt8'],
            'Tuesday': ['Tuesday', 'Alt2', 'Alt9', 'Alt9'],
            'Wednesday': ['Wednesday', 'Alt3', 'Alt5', 'Alt5'],
            'Thursday': ['Thursday', 'Alt4', 'Alt4', 'Alt4'],
            'Friday': ['Friday', 'Alt5', 'Alt5', 'Alt5'],
            'Saturday': ['Saturday', 'Alt6', 'Alt10', 'Alt10'],
            'Sunday': ['Sunday', 'Alt7', 'Alt7', 'Alt7']
        };

        let skipCount = {};

        function skipWorkout(day) {
            skipCount[day] = (skipCount[day] || 0) + 1;
            const progression = workoutProgression[day];
            const nextWorkout = progression[Math.min(skipCount[day], progression.length - 1)];
            closePopup(day);
            showWorkout(nextWorkout);
        }

        const allWorkouts = [
            { warmup: '<li>Jumping Jacks: 3x30 sec</li>', workout: '<li>Closed Grip DB Press: 22.5 lbs, 3x12</li><li>DB Floor Press: 22.5 lbs, 3x11</li><li>Overhead DB Tricep Ext: 22.5 lbs, 3x10</li><li>DB Skull Crushers: 12.5 lbs, 3x10</li><li>DB Chest Flys: 12.5 lbs, 3x12</li>' },
            { warmup: '<li>Arm Swings: 2x20</li>', workout: '<li>DB Bent Over Rows: 22.5 lbs, 3x12</li><li>DB Single Arm Row: 22.5 lbs, 3x12</li><li>DB Hammer Curls: 12.5 lbs, 3x10</li><li>DB Alternating Curls: 12.5 lbs, 3x8</li>' },
            { warmup: '<li>High Knees: 3x30 sec</li>', workout: '<li>DB Elevated Squats: 20 lbs, 3x10</li><li>DB RDLs: 15 lbs each, 3x10</li><li>DB Sumo Squats: 25 lbs, 3x12</li><li>DB Good Mornings: 30 lbs, 3x10</li>' },
            { warmup: '<li>Shoulder Rolls: 2x15</li>', workout: '<li>DB Front Raises: 8 lbs, 3x12</li><li>DB Arnold Press: 12 lbs, 3x10</li><li>DB Lateral Raises: 8 lbs, 3x10</li><li>DB Upright Rows: 12 lbs, 3x12</li>' },
            { warmup: '<li>Walking Lunges: 2x10</li>', workout: '<li>DB Glute Bridge: 25 lbs, 3x12</li><li>DB RDLs: 25 lbs, 3x12</li><li>DB Step-Ups: 15 lbs each, 3x10</li><li>DB Goblet Squats: 20 lbs, 3x12</li>' },
            { warmup: '<li>Jump Rope (or mimic): 3x1 min</li>', workout: '<li>DB Chest Press: 22.5 lbs, 3x12</li><li>DB Bent Over Rows: 22.5 lbs, 3x12</li><li>DB Squats: 20 lbs, 3x10</li><li>DB Shoulder Press: 12 lbs, 3x10</li>' },
            { warmup: '<li>Plank Hold: 3x30 sec</li>', workout: '<li>DB Chest Flys: 12.5 lbs, 3x12</li><li>DB Single Arm Row: 22.5 lbs, 3x12</li><li>DB Russian Twists: 10 lbs, 3x15</li><li>DB Deadlifts: 25 lbs, 3x10</li>' },
            { warmup: '<li>Arm Circles: 2x20</li>', workout: '<li>DB Bench Press: 25 lbs, 4x10</li><li>DB Tricep Kickbacks: 12.5 lbs, 4x12</li><li>DB Flys: 15 lbs, 4x10</li><li>DB Overhead Press: 20 lbs, 4x8</li>' },
            { warmup: '<li>Dead Hangs: 3x20 sec</li>', workout: '<li>DB Reverse Flys: 10 lbs, 4x12</li><li>DB Concentration Curls: 15 lbs, 4x10</li><li>DB Underhand Rows: 25 lbs, 4x10</li>' },
            { warmup: '<li>Leg Swings: 2x15</li>', workout: '<li>DB Lunges: 20 lbs, 4x10</li><li>DB Deadlifts: 30 lbs, 4x10</li><li>DB Side Squats: 20 lbs, 4x12</li>' },
            { warmup: '<li>Arm Swings: 2x20</li>', workout: '<li>DB Rear Delt Flys: 10 lbs, 4x12</li><li>DB Shoulder Press: 15 lbs, 4x10</li><li>DB Lateral Raises: 10 lbs, 4x12</li>' },
            { warmup: '<li>Butt Kicks: 3x30 sec</li>', workout: '<li>DB Bulgarian Split Squats: 20 lbs, 4x10</li><li>DB Glute Bridge: 30 lbs, 4x12</li><li>DB Sumo Deadlifts: 25 lbs, 4x10</li>' },
            { warmup: '<li>Dynamic Stretch: 2 min</li>', workout: '<li>DB Thrusters: 20 lbs, 4x10</li><li>DB Renegade Rows: 15 lbs, 4x12</li><li>DB Goblet Squats: 25 lbs, 4x10</li>' },
            { warmup: '<li>Plank Hold: 3x30 sec</li>', workout: '<li>DB Side Bends: 15 lbs, 4x15</li><li>DB Russian Twists: 12 lbs, 4x15</li><li>DB Leg Raises: 10 lbs, 4x12</li>' },
            { warmup: '<li>Jumping Jacks: 3x30 sec</li>', workout: '<li>DB Incline Press: 25 lbs, 4x10</li><li>DB Tricep Overhead: 15 lbs, 4x12</li><li>DB Flys: 15 lbs, 4x12</li>' },
            { warmup: '<li>Arm Swings: 2x20</li>', workout: '<li>DB Reverse Grip Rows: 25 lbs, 4x10</li><li>DB Bicep Curls: 15 lbs, 4x12</li><li>DB Single Arm Pulls: 20 lbs, 4x12</li>' },
            { warmup: '<li>High Knees: 3x30 sec</li>', workout: '<li>DB Clean & Press: 20 lbs, 4x10</li><li>DB Deadlift to Row: 25 lbs, 4x10</li><li>DB Squat to Curl: 15 lbs, 4x12</li>' }
        ];

        let currentAllIndex = 0;

        function showAllWorkouts(index) {
            closeAllPopups();
            if (index < 0) index = allWorkouts.length - 1;
            if (index >= allWorkouts.length) index = 0;
            currentAllIndex = index;
            const workout = allWorkouts[index];
            document.getElementById('all-workout-content').innerHTML = `
                <h3>Warmup (5-10 min)</h3><ul>${workout.warmup}</ul>
                <h3>Workout (45 min)</h3><ul>${workout.workout}</ul>
            `;
            document.getElementById('all-workouts').style.display = 'block';
        }

        const quotes = [
            "¡Karen, you’re a lil’ Ecuadorian star lifting her way to sparkle!",
            "Every dumbbell rep is a cute step to your dreams, darling!",
            "From Hartford to Quito, you’re twirling weights like a princess!",
            "Doing a lil’ something is better than nothing—shine on, cutie!",
            "Ecuadorian queens like you lift daily—keep it adorbs!",
            "Sweat in your cozy nook, glow like a fairy—Karen, you’re magic!",
            "Lift those lil’ weights and build a big, cute life!",
            "Hartford’s sweetest dumbbell diva—Karen, you’re unstoppable!",
            "Twirl, lift, repeat—every set’s a hug from you to you!",
            "Karen, you’re a pink-powered princess of strength!"
        ];

        function showMotivation() {
            closeAllPopups();
            const randomQuote = quotes[Math.floor(Math.random() * quotes.length)];
            document.getElementById('quote').innerText = randomQuote;
            document.getElementById('motivate').style.display = 'block';
        }
    </script>
</body>
</html>
