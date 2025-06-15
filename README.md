<h1 align="center">Olá, eu sou o Matheus Martins Ribeiro!</h1>

<p align="center">
  <strong>Desenvolvedor Full Stack em formação | Futuro Engenheiro de Software</strong><br/>
  Estudante Java - ALura | Apaixonado por tecnologia
</p>

<p align="center">
  <a href="https://github.com/MartnsProjetos" target="_blank">
    <img src="https://img.shields.io/badge/GitHub-000?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" />
  </a>
  <a href="https://www.linkedin.com/in/matheusmartnsdeveloper" target="_blank">
    <img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" />
  </a>
  <a href="https://martins-dev.netlify.app" target="_blank">
    <img src="https://img.shields.io/badge/Portfólio-111?style=for-the-badge&logo=vercel&logoColor=white" alt="Portfólio" />
  </a>
  <a href="https://instagram.com" target="_blank">
    <img src="https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white" alt="Instagram" />
  </a>
</p>

---

## Sobre mim
Tenho 18 anos, moro em São Paulo e curso o último ano do ensino médio. Me especializo em Java pela Alura, com foco em orientação a objetos, interfaces e boas práticas. Estudo de forma autodidata e desenvolvo projetos práticos com disciplina e consistência.

[**Ver meu currículo completo**](https://drive.google.com/file/d/1NIsSKXQMM-jtBu_uM1CWehjT_W96e3g5/view?usp=sharing)

---

## 🚀 Tecnologias

<p align="center">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg" width="40" height="40" title="Java" />
  <img src="https://cdn.worldvectorlogo.com/logos/nodejs-icon.svg" width="40" height="40" title="Node.js" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg" height="40" title="MySQL" />

  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" width="40" height="40" title="JavaScript" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" width="40" height="40" title="HTML" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" width="40" height="40" title="CSS" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" width="40" height="40" title="Git" />
</p>


---

<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <title>Gráfico de commits GitHub</title>
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <style>
    body { font-family: Arial, sans-serif; max-width: 700px; margin: 40px auto; }
    canvas { max-width: 100%; }
  </style>
</head>
<body>

<h2>Contribuições por Linguagem (GitHub + Uso)</h2>
<canvas id="commitsChart" width="600" height="400"></canvas>

<script>
  const username = 'MartnsProjetos';

  // Linguagens que você usa e a % inicial
  const languages = {
    Java: 70,
    'Node.js': 6,
    MySQL: 6,
    JavaScript: 6,
    HTML: 6,
    CSS: 6
  };

  // Função para buscar repositórios do usuário
  async function fetchRepos() {
    const response = await fetch(`https://api.github.com/users/${username}/repos`);
    if (!response.ok) {
      alert('Erro ao buscar repositórios do GitHub');
      return [];
    }
    return await response.json();
  }

  // Função para contar commits recentes em cada repo
  async function fetchCommits(repoName) {
    // Busca commits do último mês (30 dias)
    const since = new Date();
    since.setDate(since.getDate() - 30);
    const sinceISO = since.toISOString();

    const url = `https://api.github.com/repos/${username}/${repoName}/commits?since=${sinceISO}`;
    const response = await fetch(url);
    if (!response.ok) return [];
    return await response.json();
  }

  async function main() {
    const repos = await fetchRepos();
    // Objeto para contar commits por linguagem
    const commitCounts = {
      Java: 0,
      'Node.js': 0,
      MySQL: 0,
      JavaScript: 0,
      HTML: 0,
      CSS: 0
    };

    for (const repo of repos) {
      const lang = repo.language;
      if (!commitCounts.hasOwnProperty(lang)) continue;

      const commits = await fetchCommits(repo.name);
      commitCounts[lang] += commits.length;
    }

    // Agora vamos combinar o uso (percentual fixo) + commits da API
    // Para visualizar, vamos somar o uso + commits (normalizando commits)

    // Normaliza commits para escala 0-30 (arbitrário)
    const maxCommits = Math.max(...Object.values(commitCounts), 1);
    for (const lang in commitCounts) {
      // Normaliza a 30%
      commitCounts[lang] = (commitCounts[lang] / maxCommits) * 30;
    }

    // Soma uso + commits normalizados
    const finalData = {};
    for (const lang in languages) {
      finalData[lang] = languages[lang] + (commitCounts[lang] || 0);
    }

    renderChart(finalData);
  }

  function renderChart(data) {
    const ctx = document.getElementById('commitsChart').getContext('2d');
    new Chart(ctx, {
      type: 'bar',
      data: {
        labels: Object.keys(data),
        datasets: [{
          label: 'Contribuição (%)',
          data: Object.values(data),
          backgroundColor: [
            '#5382a1', // Java - azul
            '#3c873a', // Node - verde
            '#f29111', // MySQL - laranja
            '#f0db4f', // JS - amarelo
            '#e44d26', // HTML - vermelho
            '#264de4'  // CSS - azul
          ],
          borderRadius: 5,
        }]
      },
      options: {
        scales: {
          y: {
            beginAtZero: true,
            max: 100
          }
        },
        plugins: {
          legend: { display: false },
          tooltip: { enabled: true }
        }
      }
    });
  }

  main();

</script>
</body>
</html>

---

## 📬 Contato

- **Email**: mtz.martinss03@gmail.com  
- **WhatsApp**: [Clique aqui para conversar](https://wa.me/5511963822159)  
- **LinkedIn**: [linkedin.com/in/matheusmartnsdeveloper](https://www.linkedin.com/in/matheusmartnsdeveloper)  
- **Portfólio**: [martins-dev.netlify.app](https://martins-dev.netlify.app/)

---

<p align="center"><em>“Transforme problemas. Codifique soluções.”</em><br/>— Matheus Martins</p> 
