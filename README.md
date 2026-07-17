# MCFB-27<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <title>MCFB 27</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />

  <!-- Basic styling -->
  <style>
    html, body {
      margin: 0;
      padding: 0;
      background: #000;
      color: #fff;
      font-family: Arial, sans-serif;
      height: 100%;
      overflow: hidden;
    }
    #unity-container {
      width: 100vw;
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #111;
    }
    #unity-canvas {
      width: 100%;
      height: 100%;
      background: #000;
    }
    #loading {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      font-size: 18px;
      color: #fff;
    }
  </style>
</head>
<body>
  <div id="unity-container">
    <canvas id="unity-canvas"></canvas>
    <div id="loading">Loading MCFB 27...</div>
  </div>

  <!-- Unity loader script (from your Build folder) -->
  <script>
    // CHANGE THESE NAMES to match your actual Unity build files
    const buildUrl = "Build";
    const loaderUrl = buildUrl + "/MCFB27.loader.js";
    const config = {
      dataUrl: buildUrl + "/MCFB27.data",
      frameworkUrl: buildUrl + "/MCFB27.framework.js",
      codeUrl: buildUrl + "/MCFB27.wasm",
      streamingAssetsUrl: "StreamingAssets",
      companyName: "YourStudio",
      productName: "MCFB 27",
      productVersion: "1.0",
    };

    const canvas = document.getElementById("unity-canvas");
    const loading = document.getElementById("loading");

    const script = document.createElement("script");
    script.src = loaderUrl;
    script.onload = () => {
      createUnityInstance(canvas, config).then(() => {
        loading.style.display = "none";
      }).catch((message) => {
        loading.innerText = "Error loading game: " + message;
      });
    };
    document.body.appendChild(script);
  </script>
</body>
</html>
