<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Stopwatch</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background-color: #f0f4f8;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
    }

    h1 {
      font-size: 3em;
      margin-bottom: 20px;
    }

    .timer {
      font-size: 4em;
      margin-bottom: 30px;
    }

    .buttons {
      display: flex;
      gap: 15px;
    }

    button {
      padding: 10px 20px;
      font-size: 1em;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: background 0.2s;
    }

    button.start { background-color: #28a745; color: white; }
    button.pause { background-color: #ffc107; color: black; }
    button.reset { background-color: #dc3545; color: white; }

    button:hover {
      opacity: 0.9;
    }
  </style>
</head>
<body>

  <h1>Stopwatch</h1>
  <div class="timer" id="display">00:00:00</div>
  <div class="buttons">
    <button class="start" onclick="start()">Start</button>
    <button class="pause" onclick="pause()">Pause</button>
    <button class="reset" onclick="reset()">Reset</button>
  </div>

  <script>
    let [seconds, minutes, hours] = [0, 0, 0];
    let display = document.getElementById("display");
    let timer = null;

    function stopwatch() {
      seconds++;
      if (seconds === 60) {
        seconds = 0;
        minutes++;
        if (minutes === 60) {
          minutes = 0;
          hours++;
        }
      }

      let h = hours < 10 ? "0" + hours : hours;
      let m = minutes < 10 ? "0" + minutes : minutes;
      let s = seconds < 10 ? "0" + seconds : seconds;

      display.innerText = `${h}:${m}:${s}`;
    }

    function start() {
      if (timer !== null) {
        clearInterval(timer);
      }
      timer = setInterval(stopwatch, 1000);
    }

    function pause() {
      clearInterval(timer);
    }

    function reset() {
      clearInterval(timer);
      [seconds, minutes, hours] = [0, 0, 0];
      display.innerText = "00:00:00";
    }
  </script>

</body>
</html>