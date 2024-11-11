<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>Junw0701의 GitHub 프로젝트</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
  <!-- Font Awesome for Icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <style>
    /* Reset 기본 스타일 */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Roboto', sans-serif;
      background-color: #f0f2f5;
      color: #333;
      line-height: 1.6;
    }

    /* 네비게이션 바 */
    .navbar {
      position: fixed;
      top: 0;
      width: 100%;
      background-color: #ffffff;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
      z-index: 1000;
    }

    .navbar-container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 10px 20px;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .navbar-logo {
      font-size: 1.5em;
      font-weight: bold;
      color: #24292e;
      text-decoration: none;
    }

    .navbar-links a {
      margin-left: 20px;
      text-decoration: none;
      color: #24292e;
      font-weight: 500;
      transition: color 0.3s;
    }

    .navbar-links a:hover {
      color: #0366d6;
    }

    /* 배너 섹션 */
    .banner {
      background: url('https://via.placeholder.com/1200x400') center/cover no-repeat;
      height: 400px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: #ffffff;
      text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
      margin-top: 60px; /* 네비게이션 바 높이 */
    }

    .banner h1 {
      font-size: 3em;
      text-align: center;
    }

    /* 그리드 레이아웃 */
    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
      gap: 20px;
      padding: 40px 20px;
      max-width: 1200px;
      margin: 0 auto;
    }

    /* 카드 디자인 */
    .card {
      background-color: #ffffff;
      border-radius: 8px;
      overflow: hidden;
      box-shadow: 0 4px 6px rgba(0,0,0,0.1);
      transition: transform 0.3s, box-shadow 0.3s;
      display: flex;
      flex-direction: column;
    }

    .card:hover {
      transform: translateY(-5px);
      box-shadow: 0 8px 12px rgba(0,0,0,0.2);
    }

    .card img {
      width: 100%;
      height: 180px;
      object-fit: cover;
    }

    .card-content {
      padding: 20px;
      flex: 1;
      display: flex;
      flex-direction: column;
    }

    .card-title {
      font-size: 1.2em;
      margin-bottom: 10px;
      color: #24292e;
    }

    .card-description {
      flex: 1;
      color: #555555;
      margin-bottom: 15px;
    }

    .card-link {
      text-align: right;
    }

    .card-link a {
      display: inline-block;
      padding: 10px 15px;
      background-color: #0366d6;
      color: #ffffff;
      text-decoration: none;
      border-radius: 4px;
      transition: background-color 0.3s;
      font-weight: 500;
    }

    .card-link a:hover {
      background-color: #024eaf;
    }

    /* 푸터 */
    .footer {
      background-color: #ffffff;
      padding: 20px;
      text-align: center;
      box-shadow: 0 -2px 4px rgba(0,0,0,0.1);
      margin-top: 40px;
    }

    .footer p {
      color: #555555;
    }

    /* 반응형 디자인 */
    @media (max-width: 768px) {
      .banner h1 {
        font-size: 2em;
      }

      .navbar-container {
        flex-direction: column;
        align-items: flex-start;
      }

      .navbar-links {
        margin-top: 10px;
      }

      .navbar-links a {
        margin-left: 0;
        margin-right: 15px;
      }
    }
  </style>
</head>
<body>
  <!-- 네비게이션 바 -->
  <nav class="navbar">
    <div class="navbar-container">
      <a href="#" class="navbar-logo">Junw0701</a>
      <div class="navbar-links">
        <a href="#projects">Projects</a>
        <a href="https://github.com/junw0701" target="_blank"><i class="fab fa-github"></i> GitHub</a>
        <a href="https://www.linkedin.com/in/yourprofile" target="_blank"><i class="fab fa-linkedin"></i> LinkedIn</a>
      </div>
    </div>
  </nav>

  <!-- 배너 섹션 -->
  <section class="banner">
    <h1>Welcome to My GitHub Projects</h1>
  </section>

  <!-- 그리드 레이아웃 -->
  <section id="projects" class="grid" id="repoGrid">
    <!-- 프로젝트 카드가 여기에 삽입됩니다 -->
  </section>

  <!-- 푸터 -->
  <footer class="footer">
    <p>&copy; 2024 Junw0701. All rights reserved.</p>
  </footer>

  <!-- Font Awesome Script -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/js/all.min.js" integrity="sha512-..." crossorigin="anonymous" referrerpolicy="no-referrer"></script>

  <script>
    fetch('https://api.github.com/users/junw0701/repos')
      .then(response => response.json())
      .then(data => {
        const grid = document.getElementById('repoGrid');
        data.forEach(repo => {
          const card = document.createElement('div');
          card.className = 'card';
          
          // 썸네일 이미지 설정 (프로젝트의 홈페이지나 README에 이미지가 있다면 사용)
          let thumbnail = 'https://via.placeholder.com/300x180?text=Project+Thumbnail';
          if (repo.homepage) {
            thumbnail = repo.homepage;
          }

          card.innerHTML = `
            <img src="${thumbnail}" alt="${repo.name} Thumbnail">
            <div class="card-content">
              <h3 class="card-title">${repo.name}</h3>
              <p class="card-description">${repo.description || 'No description provided.'}</p>
              <div class="card-link">
                <a href="${repo.html_url}" target="_blank"><i class="fas fa-external-link-alt"></i> View on GitHub</a>
              </div>
            </div>
          `;
          grid.appendChild(card);
        });
      })
      .catch(error => console.error('Error fetching repositories:', error));
  </script>
</body>
</html>
