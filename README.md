<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Para Dafne ❤️</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      font-family: Arial, sans-serif;
      overflow: hidden;
      background: linear-gradient(135deg, #ff4d6d, #a64dff);
    }

    .corazones {
      position: fixed;
      width: 100%;
      height: 100%;
      z-index: 1;
      pointer-events: none;
    }

    .corazon {
      position: absolute;
      color: purple;
      animation: flotar linear infinite;
    }

    @keyframes flotar {
      0% { transform: translateY(100vh); opacity: 1; }
      100% { transform: translateY(-10vh); opacity: 0; }
    }

    .contenedor {
      position: relative;
      z-index: 2;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100%;
    }

    .texto {
      color: black;
      font-size: 2.2rem;
      text-align: center;
      max-width: 80%;
    }

    .final {
      font-size: 2.5rem;
      animation: latido 1s infinite;
    }

    @keyframes latido {
      0% { transform: scale(1); }
      50% { transform: scale(1.1); }
      100% { transform: scale(1); }
    }
  </style>
</head>
<body>

  <div class="corazones" id="corazones"></div>

  <div class="contenedor">
    <div class="texto" id="texto"></div>
  </div>

  <script>
    const textos = [
      "Hola Dafne",
      "Hay algo que quiero decirte...",
      "Desde hace un tiempo me haces muy feliz",
      "Me encanta pasar tiempo contigo",
      "Y la verdad no quiero seguir guardándomelo...",
      "Esto es importante...",
      "¿Quieres ser mi novia?"
    ];

    let indice = 0;
    const textoDiv = document.getElementById("texto");

    // ✍️ EFECTO LETRA POR LETRA
    function escribirTexto(texto, callback) {
      textoDiv.textContent = "";
      let i = 0;

      const intervalo = setInterval(() => {
        textoDiv.textContent += texto[i];
        i++;

        if (i >= texto.length) {
          clearInterval(intervalo);
          if (callback) callback();
        }
      }, 70);
    }

    function cambiarTexto() {
      if (indice === textos.length - 1) {
        textoDiv.classList.add("final");
        escribirTexto(textos[indice]);
        return;
      }

      indice++;

      escribirTexto(textos[indice], () => {
        let tiempo = (indice === textos.length - 2) ? 6000 : 3000;
        setTimeout(cambiarTexto, tiempo);
      });
    }

    // INICIO
    escribirTexto(textos[0], () => {
      setTimeout(cambiarTexto, 3000);
    });

    // ❤️ CORAZONES
    const contenedor = document.getElementById("corazones");

    function crearCorazon() {
      const corazon = document.createElement("div");
      corazon.classList.add("corazon");
      corazon.innerHTML = "❤";

      corazon.style.left = Math.random() * 100 + "vw";
      corazon.style.fontSize = (Math.random() * 20 + 15) + "px";
      corazon.style.animationDuration = (Math.random() * 3 + 4) + "s";

      contenedor.appendChild(corazon);

      setTimeout(() => {
        corazon.remove();
      }, 7000);
    }

    setInterval(crearCorazon, 300);
  </script>

</body>
</html>
