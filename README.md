<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Feeding Bear</title>
<style>
  body {
    background: #eef;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
  }

  /* Bear container */
  #bear-container {
    position: relative;
    width: 200px;
    height: 250px;
    margin-bottom: 30px;
    transition: transform 0.3s ease;
  }

  /* Bear body (simple square for example) */
  #bear {
    width: 100%;
    height: 100%;
    background: #773311; /* brown */
    border-radius: 10px;
    position: relative;
  }

  /* Bear mouth (chewing or open) */
  #mouth {
    position: absolute;
    bottom: 70px;
    left: 50%;
    transform: translateX(-50%);
    width: 40px;
    height: 10px;
    background: red;
    border-radius: 5px;
    transition: all 0.2s;
  }

  /* Donut element */
  #donut {
    width: 40px;
    height: 40px;
    background: pink;
    border-radius: 50%;
    cursor: pointer;
    margin-bottom: 20px;
    animation: popIn 0.5s ease forwards;
    position: relative;
  }

  /* Reappear with a woosh */
  @keyframes popIn {
    from { transform: scale(0); opacity: 0; }
    to { transform: scale(1); opacity: 1; }
  }

</style>
</head>
<body>

<div id="donut"></div>
<div id="bear-container">
  <div id="bear">
    <div id="mouth"></div>
  </div>
</div>

<script>
  const donut = document.getElementById('donut');
  const bear = document.getElementById('bear');
  const mouth = document.getElementById('mouth');

  let sizeMultiplier = 1;

  function feedBear() {
    // Change mouth to chewing
    mouth.style.background = 'darkred';
    mouth.style.height = '20px';

    // Grow the bear
    sizeMultiplier += 0.2; // Increase size
    bear.style.transform = `scale(${sizeMultiplier})`;

    // Animate donut (simulate magic/woosh)
    donut.style.animation = 'popIn 0.5s ease';

    // Reset mouth after chewing
    setTimeout(() => {
      mouth.style.background = 'red';
      mouth.style.height = '10px';
    }, 300);
  }

  donut.addEventListener('click', () => {
    feedBear();

    // Reappear donut with animation
    donut.style.transform = 'scale(0)';
    setTimeout(() => {
      donut.style.transform = 'scale(1)';
    }, 300);
  });
</script>

</body>
</html>
