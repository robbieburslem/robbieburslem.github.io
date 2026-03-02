<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>3D Model Viewer Demo</title>

  <!-- Load model-viewer -->
  <script type="module"
    src="/Projects/Test/Escapement_Wheel_1.glb>
  </script>

  <style>
    body {
      margin: 0;
      background: #111;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      color: white;
      font-family: Arial, sans-serif;
    }

    model-viewer {
      width: 500px;
      height: 500px;
    }
  </style>
</head>
<body>

  <model-viewer
    src="https://modelviewer.dev/shared-assets/models/Astronaut.glb"
    alt="3D Astronaut"
    auto-rotate
    camera-controls
    shadow-intensity="1">
  </model-viewer>

</body>
</html>
