<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <title>Malla Curricular - Ingeniería en Nanotecnología</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background: #f0faff;
      font-family: 'Segoe UI', sans-serif;
      color: #333;
    }

    header {
      background: #30d5c8; /* azul turquesa */
      padding: 20px;
      text-align: center;
      color: white;
      font-size: 28px;
      font-weight: bold;
    }

    .container {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
      padding: 40px;
    }

    .semestre {
      background: white;
      border-radius: 12px;
      padding: 20px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }

    .semestre h2 {
      color: #30d5c8;
      margin-top: 0;
    }

    .ramo {
      display: block;
      background-color: #87ceeb; /* azul cielo */
      color: white;
      padding: 10px 15px;
      border-radius: 8px;
      margin: 8px 0;
      cursor: pointer;
      transition: all 0.3s ease;
      text-align: center;
      font-weight: 500;
    }

    .ramo:hover {
      background-color: #5ec6dd;
      transform: scale(1.05);
    }

    .ramo.tachado {
      text-decoration: line-through;
      background-color: #add8e6; /* azul celeste */
      opacity: 0.7;
      cursor: default;
    }

    .ramo.bloqueado {
      background-color: #a0aec0;
      cursor: not-allowed;
      opacity: 0.5;
    }
  </style>
</head>
<body>
  <header>
    Ingeniería en Nanotecnología - Malla Curricular Interactiva
  </header>

  <div class="container" id="malla"></div>

  <script>
    const ramos = {
      "1": ["Química inorgánica", "Probabilidad y estadística", "Taller de ética", "Calculo diferencial", "Lógica de programación", "Seminario de introducción a la nanotecnología"],
      "2": ["Química analítica", "Ciencias e ingeniería de los materiales", "mecánica clásica", "Calculo integral", "Fundamentos de química orgánica", "Fundamentos de la investigación"],
      "3": ["Algebra lineal", "Fundamentos de biología", "Ondas y calor", "Calculo vectorial", "química orgánica II", "Estancias de estudio y desarrollo profesional I"],
      "4": ["Análisis instrumental", "Biología molecular", "Física del estado sólido", "Ecuaciones diferenciales", "Electromagnetismo", "Taller de investigación I"],
      "5": ["fisicoquímica", "Nanobiología I", "Nanofísica I", "Análisis numérico", "Nanoquímica I", "Estancias de estudio y desarrollo profesional II"],
      "6": ["Desarrollo sustentable", "Nanobiología II", "Nanofísica II", "caracterización de los materiales", "Nanoquímica II", "Taller de investigación II"],
      "7": ["Introducción al modelado por computadora", "Microbiología", "Tópicos de ingeniería y tecnología I", "Tópicos de ingeniería y tecnología II", "Química ambiental", "Estancias de estudio y desarrollo profesional III", "Síntesis de nanomateriales"],
      "8": ["Tópicos de ingeniería y tecnología III", "Tópicos de ingeniería y tecnología IV", "Tópicos de ingeniería y tecnología V", "Bioprocesos", "Introducción a la anatomía y fisiología humana", "Introducción a la biotecnología", "Introducción a los biomateriales"]
    };

    const dependencias = {
      "Química analítica": ["Química inorgánica"],
      "Calculo integral": ["Calculo diferencial"],
      "química orgánica II": ["Fundamentos de química orgánica"],
      "Calculo vectorial": ["Calculo integral"],
      "Análisis instrumental": ["Química analítica"],
      "Biología molecular": ["Fundamentos de biología"],
      "Ecuaciones diferenciales": ["Calculo vectorial"],
      "Electromagnetismo": ["Calculo vectorial"],
      "Taller de investigación I": ["Fundamentos de la investigación"],
      "Nanobiología I": ["Biología molecular"],
      "Análisis numérico": ["Análisis instrumental"],
      "Estancias de estudio y desarrollo profesional II": ["Estancias de estudio y desarrollo profesional I"],
      "Nanobiología II": ["Nanobiología I"],
      "Nanofísica II": ["Nanofísica I"],
      "Nanoquímica II": ["Nanoquímica I"],
      "Taller de investigación II": ["Taller de investigación I"],
      "Microbiología": ["Nanobiología II"],
      "Estancias de estudio y desarrollo profesional III": ["Estancias de estudio y desarrollo profesional II"],
      "Síntesis de nanomateriales": ["caracterización de los materiales"],
      "Tópicos de ingeniería y tecnología III": ["Tópicos de ingeniería y tecnología I", "Tópicos de ingeniería y tecnología II"],
      "Tópicos de ingeniería y tecnología IV": ["Tópicos de ingeniería y tecnología I", "Tópicos de ingeniería y tecnología II"],
      "Tópicos de ingeniería y tecnología V": ["Tópicos de ingeniería y tecnología I", "Tópicos de ingeniería y tecnología II"]
    };

    const estado = {};
    const mallaDiv = document.getElementById("malla");

    for (const semestre in ramos) {
      const semDiv = document.createElement("div");
      semDiv.className = "semestre";
      const h2 = document.createElement("h2");
      h2.textContent = `Semestre ${semestre}`;
      semDiv.appendChild(h2);

      ramos[semestre].forEach(ramo => {
        const div = document.createElement("div");
        div.textContent = ramo;
        div.className = "ramo";
        div.id = ramo;
        estado[ramo] = false;

        if (dependencias[ramo]) {
          div.classList.add("bloqueado");
        }

        div.addEventListener("click", () => {
          if (div.classList.contains("bloqueado")) {
            alert("Este ramo está bloqueado por prerrequisitos.");
            return;
          }
          if (!estado[ramo]) {
            div.classList.add("tachado");
            estado[ramo] = true;

            for (let [sig, requisitos] of Object.entries(dependencias)) {
              if (!estado[sig]) {
                const completos = requisitos.every(r => estado[r]);
                if (completos) {
                  document.getElementById(sig).classList.remove("bloqueado");
                }
              }
            }
          }
        });

        semDiv.appendChild(div);
      });

      mallaDiv.appendChild(semDiv);
    }
  </script>
</body>
</html>
