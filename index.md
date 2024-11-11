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
      background-color: #f9f9f9;
      color: #333;
      display: flex;
      overflow-x: hidden;
    }

    /* 사이드바 */
    .sidebar {
      width: 250px;
      background: linear-gradient(135deg, #24292e, #1b1f23);
      color: #ffffff;
      min-height: 100vh;
      position: fixed;
      left: 0;
      top: 0;
      padding: 30px 20px;
      display: flex;
      flex-direction: column;
      align-items: center;
      transition: width 0.3s;
    }

    .sidebar .profile {
      text-align: center;
      margin-bottom: 50px;
      animation: fadeInLeft 1s ease-out;
    }

    .sidebar .profile img {
      width: 120px;
      height: 120px;
      border-radius: 50%;
      margin-bottom: 15px;
      border: 3px solid #ffffff;
      transition: transform 0.3s;
    }

    .sidebar .profile img:hover {
      transform: scale(1.05);
    }

    .sidebar .profile h2 {
      font-size: 1.3em;
      margin-bottom: 10px;
      transition: color 0.3s;
    }

    .sidebar .profile h2:hover {
      color: #ff0000;
    }

    .sidebar .profile a {
      color: #ffffff;
      text-decoration: none;
      font-size: 1.1em;
      display: flex;
      align-items: center;
      justify-content: center;
      margin-top: 10px;
      transition: color 0.3s;
    }

    .sidebar .profile a i {
      margin-right: 8px;
      transition: transform 0.3s;
    }

    .sidebar .profile a:hover {
      color: #ff0000;
    }

    .sidebar .profile a:hover i {
      transform: rotate(20deg);
    }

    /* 메인 콘텐츠 */
    .main-content {
      margin-left: 250px; /* 사이드바 너비와 동일 */
      width: calc(100% - 250px);
      display: flex;
      flex-direction: column;
      min-height: 100vh;
      background: linear-gradient(180deg, #ffffff, #f0f0f0);
      transition: margin-left 0.3s, width 0.3s;
    }

    /* 네비게이션 바 */
    .navbar {
      background-color: rgba(255, 255, 255, 0.95);
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
      z-index: 1000;
      width: 100%;
      position: sticky;
      top: 0;
      animation: fadeInDown 1s ease-out;
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
      font-size: 1.8em;
      font-weight: bold;
      color: #24292e;
      text-decoration: none;
      transition: color 0.3s;
    }

    .navbar-logo:hover {
      color: #ff0000;
    }

    .navbar-links a {
      margin-left: 25px;
      text-decoration: none;
      color: #24292e;
      font-weight: 500;
      transition: color 0.3s;
      display: flex;
      align-items: center;
    }

    .navbar-links a i {
      margin-right: 8px;
      transition: transform 0.3s;
    }

    .navbar-links a:hover {
      color: #ff0000; /* 유튜브 레드 */
    }

    .navbar-links a:hover i {
      transform: translateY(-3px);
    }

    /* 배너 섹션 */
    .banner {
      background: linear-gradient(135deg, rgba(255,0,0,0.7), rgba(0,0,0,0.7)), url('https://via.placeholder.com/1200x400') center/cover no-repeat;
      height: 400px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: #ffffff;
      text-shadow: 2px 2px 6px rgba(0,0,0,0.7);
      margin-top: 0; /* 네비게이션 바 높이 제거 */
      animation: fadeIn 2s ease-out;
    }

    .banner h1 {
      font-size: 3em;
      text-align: center;
      color: #ffffff;
      padding: 20px;
      background: rgba(0, 0, 0, 0.4);
      border-radius: 10px;
      transition: transform 0.3s;
    }

    .banner h1:hover {
      transform: scale(1.05);
    }

    /* 그리드 레이아웃 */
    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
      gap: 25px;
      padding: 60px 20px;
      max-width: 1200px;
      margin: 0 auto;
      animation: fadeInUp 1.5s ease-out;
    }

    /* 카드 디자인 */
    .card {
      background-color: #ffffff;
      border-radius: 12px;
      overflow: hidden;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
      transition: transform 0.3s, box-shadow 0.3s;
      display: flex;
      flex-direction: column;
      border: 1px solid #e0e0e0;
    }

    .card:hover {
      transform: translateY(-10px);
      box-shadow: 0 12px 16px rgba(0,0,0,0.2);
    }

    .card img {
      width: 100%;
      height: 180px;
      object-fit: cover;
      background-color: #f0f0f0;
      transition: opacity 0.3s;
    }

    .card:hover img {
      opacity: 0.9;
    }

    .card-content {
      padding: 20px;
      flex: 1;
      display: flex;
      flex-direction: column;
    }

    .card-title {
      font-size: 1.4em;
      margin-bottom: 10px;
      color: #24292e;
      text-decoration: none;
      transition: color 0.3s;
    }

    .card-title:hover {
      color: #ff0000; /* 유튜브 레드 */
    }

    .card-description {
      flex: 1;
      color: #555555;
      margin-bottom: 15px;
      font-size: 1em;
      line-height: 1.5;
    }

    .card-info {
      display: flex;
      justify-content: flex-start;
      gap: 15px;
      margin-bottom: 15px;
      animation: fadeIn 1s ease-in;
    }

    .repo-language, .repo-stars {
      background-color: #f1f1f1;
      padding: 6px 12px;
      border-radius: 20px;
      font-size: 0.9em;
      display: flex;
      align-items: center;
      transition: background-color 0.3s;
    }

    .repo-language {
      background: linear-gradient(135deg, #ff4b2b, #ff416c);
      color: #ffffff;
    }

    .repo-stars {
      background-color: #ffd700;
      color: #333333;
    }

    .repo-stars i {
      margin-right: 5px;
      color: #ffcc00;
    }

    .card-link {
      text-align: right;
      animation: fadeIn 1s ease-in;
    }

    .card-link a {
      display: inline-block;
      padding: 10px 15px;
      background: linear-gradient(135deg, #ff4b2b, #ff416c); /* 유튜브 레드 그라데이션 */
      color: #ffffff;
      text-decoration: none;
      border-radius: 4px;
      transition: background 0.3s, transform 0.3s;
      font-weight: 500;
      font-size: 0.95em;
    }

    .card-link a:hover {
      background: linear-gradient(135deg, #cc0000, #b30000);
      transform: translateY(-2px);
    }

    /* 커밋 로그 섹션 */
    .commits-section {
      padding: 40px 20px;
      max-width: 1200px;
      margin: 0 auto;
      animation: fadeInUp 1.5s ease-out;
    }

    .commits-section h2 {
      margin-bottom: 30px;
      color: #24292e;
      font-size: 2.5em;
      border-bottom: 3px solid #e0e0e0;
      padding-bottom: 10px;
      display: inline-block;
      transition: color 0.3s;
    }

    .commits-section h2:hover {
      color: #ff0000;
    }

    .commit {
      background-color: #ffffff;
      border-radius: 8px;
      padding: 20px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
      margin-bottom: 20px;
      display: flex;
      align-items: center;
      border-left: 5px solid #ff0000; /* 유튜브 레드 포인트 */
      transition: background-color 0.3s, transform 0.3s;
    }

    .commit:hover {
      background-color: #f9f9f9;
      transform: translateY(-3px);
    }

    .commit .avatar {
      margin-right: 20px;
      flex-shrink: 0;
      transition: transform 0.3s;
    }

    .commit .avatar img {
      width: 60px;
      height: 60px;
      border-radius: 50%;
      border: 2px solid #e0e0e0;
      transition: transform 0.3s;
    }

    .commit:hover .avatar img {
      transform: scale(1.05);
    }

    .commit .commit-info {
      flex: 1;
    }

    .commit .commit-info h4 {
      margin-bottom: 8px;
      color: #0366d6;
      font-size: 1.1em;
      cursor: pointer;
      transition: color 0.3s;
    }

    .commit .commit-info h4:hover {
      color: #ff0000; /* 유튜브 레드 */
      text-decoration: underline;
    }

    .commit .commit-info p {
      color: #555555;
      font-size: 0.95em;
      margin-bottom: 8px;
    }

    .commit .commit-info a {
      color: #0366d6;
      text-decoration: none;
      transition: color 0.3s;
    }

    .commit .commit-info a:hover {
      color: #ff0000;
    }

    .commit .commit-date {
      color: #999999;
      font-size: 0.85em;
      white-space: nowrap;
      transition: color 0.3s;
    }

    .commit:hover .commit-date {
      color: #666666;
    }

    /* 푸터 */
    .footer {
      background-color: #24292e;
      padding: 30px 20px;
      text-align: center;
      box-shadow: 0 -2px 4px rgba(0,0,0,0.1);
      margin-top: 40px;
      color: #ffffff;
      animation: fadeInUp 1s ease-out;
    }

    .footer p {
      color: #cccccc;
      font-size: 0.9em;
    }

    /* 애니메이션 정의 */
    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }

    @keyframes fadeInUp {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    @keyframes fadeInDown {
      from { opacity: 0; transform: translateY(-20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    /* 반응형 디자인 */
    @media (max-width: 1200px) {
      .sidebar {
        width: 200px;
      }

      .main-content {
        margin-left: 200px;
        width: calc(100% - 200px);
      }
    }

    @media (max-width: 992px) {
      .navbar-container {
        flex-direction: column;
        align-items: flex-start;
      }

      .navbar-links {
        margin-top: 10px;
        display: flex;
        flex-wrap: wrap;
      }

      .navbar-links a {
        margin-left: 0;
        margin-right: 15px;
        margin-bottom: 10px;
      }

      .grid {
        padding: 40px 10px;
      }

      .commits-section h2 {
        font-size: 2em;
      }
    }

    @media (max-width: 768px) {
      .sidebar {
        width: 60px;
        padding: 15px 10px;
      }

      .sidebar .profile h2,
      .sidebar .profile a {
        display: none;
      }

      .main-content {
        margin-left: 60px;
        width: calc(100% - 60px);
      }

      .banner h1 {
        font-size: 2em;
        padding: 10px;
      }

      .card img {
        height: 150px;
      }

      .card-description {
        font-size: 0.9em;
      }

      .commit .commit-info h4 {
        font-size: 1em;
      }

      .commit .commit-info p,
      .commit .commit-date {
        font-size: 0.8em;
      }
    }
  </style>
</head>
<body>
  <!-- 사이드바 -->
  <aside class="sidebar">
    <div class="profile">
      <img src="https://github.com/junw0701.png" alt="Profile Picture">
      <h2>Junw0701</h2>
      <a href="https://github.com/junw0701" target="_blank"><i class="fab fa-github"></i> GitHub</a>
      <a href="https://www.linkedin.com/in/yourprofile" target="_blank"><i class="fab fa-linkedin"></i> LinkedIn</a>
    </div>
  </aside>

  <!-- 메인 콘텐츠 -->
  <div class="main-content">
    <!-- 네비게이션 바 -->
    <nav class="navbar">
      <div class="navbar-container">
        <a href="#" class="navbar-logo">Junw0701</a>
        <div class="navbar-links">
          <a href="#projects"><i class="fas fa-project-diagram"></i> Projects</a>
          <a href="https://github.com/junw0701" target="_blank"><i class="fab fa-github"></i> GitHub</a>
          <a href="https://www.linkedin.com/in/yourprofile" target="_blank"><i class="fab fa-linkedin"></i> LinkedIn</a>
          <!-- 노션 링크 추가 -->
          <a href="https://flannel-toast-a5d.notion.site/DevelopLog-19ad4131a8e44e549aeda18bd346a2f5?pvs=74" target="_blank"><i class="fas fa-book"></i> Develop Log</a>
        </div>
      </div>
    </nav>

    <!-- 배너 섹션 -->
    <section class="banner">
      <h1>Welcome to My GitHub Projects</h1>
    </section>

    <!-- 그리드 레이아웃 -->
    <section id="projects" class="grid">
      <!-- 프로젝트 카드가 여기에 삽입됩니다 -->
    </section>

    <!-- 커밋 로그 섹션 -->
    <section class="commits-section">
      <h2>Latest Commit Logs</h2>
      <div id="commitLogs">
        <!-- 커밋 로그가 여기에 삽입됩니다 -->
      </div>
    </section>

    <!-- 푸터 -->
    <footer class="footer">
      <p>&copy; 2024 Junw0701. All rights reserved.</p>
    </footer>
  </div>

  <!-- Font Awesome Script -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/js/all.min.js" integrity="sha512-..." crossorigin="anonymous" referrerpolicy="no-referrer"></script>

  <script>
    // GitHub 사용자 이름
    const username = 'junw0701';

    // 프로젝트 그리드에 저장소 데이터 추가
    fetch(`https://api.github.com/users/${username}/repos?per_page=100`)
      .then(response => response.json())
      .then(data => {
        const grid = document.getElementById('projects');
        data.forEach(repo => {
          const card = document.createElement('div');
          card.className = 'card';
          
          // 썸네일 이미지 설정 (프로젝트의 homepage나 README에 이미지가 있다면 사용)
          let thumbnail = 'https://via.placeholder.com/300x180?text=Project+Thumbnail';
          if (repo.homepage) {
            thumbnail = repo.homepage;
          }

          // 저장소 언어 및 스타 수 추가
          const language = repo.language ? `<span class="repo-language">${repo.language}</span>` : '';
          const stars = `<span class="repo-stars"><i class="fas fa-star"></i> ${repo.stargazers_count}</span>`;

          card.innerHTML = `
            <img src="${thumbnail}" alt="${repo.name} Thumbnail">
            <div class="card-content">
              <a href="${repo.html_url}" target="_blank" class="card-title">${repo.name}</a>
              <p class="card-description">${repo.description || 'No description provided.'}</p>
              <div class="card-info">
                ${language}
                ${stars}
              </div>
              <div class="card-link">
                <a href="${repo.html_url}" target="_blank"><i class="fas fa-external-link-alt"></i> View on GitHub</a>
              </div>
            </div>
          `;
          grid.appendChild(card);
        });
      })
      .catch(error => console.error('Error fetching repositories:', error));

    // 커밋 로그 섹션에 커밋 데이터 추가
    fetch(`https://api.github.com/users/${username}/repos?per_page=100`)
      .then(response => response.json())
      .then(repos => {
        const commitLogsContainer = document.getElementById('commitLogs');

        // 각 저장소의 최신 커밋을 가져옵니다
        repos.forEach(repo => {
          fetch(`https://api.github.com/repos/${username}/${repo.name}/commits?per_page=1`)
            .then(response => response.json())
            .then(commits => {
              if (commits && commits.length > 0) {
                const latestCommit = commits[0];
                const commit = document.createElement('div');
                commit.className = 'commit';

                commit.innerHTML = `
                  <div class="avatar">
                    <img src="${latestCommit.author ? latestCommit.author.avatar_url : 'https://via.placeholder.com/60'}" alt="Author Avatar">
                  </div>
                  <div class="commit-info">
                    <h4 title="${latestCommit.commit.message}">${latestCommit.commit.message.length > 50 ? latestCommit.commit.message.substring(0, 50) + '...' : latestCommit.commit.message}</h4>
                    <p>Repository: <a href="${repo.html_url}" target="_blank">${repo.name}</a></p>
                  </div>
                  <div class="commit-date">
                    ${new Date(latestCommit.commit.author.date).toLocaleString()}
                  </div>
                `;
                commitLogsContainer.appendChild(commit);
              }
            })
            .catch(error => console.error(`Error fetching commits for ${repo.name}:`, error));
        });
      })
      .catch(error => console.error('Error fetching repositories for commits:', error));
  </script>
</body>
</html>
