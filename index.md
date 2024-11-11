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
    }

    /* 사이드바 */
    .sidebar {
      width: 250px;
      background-color: #24292e;
      color: #ffffff;
      min-height: 100vh;
      position: fixed;
      left: 0;
      top: 0;
      padding: 20px;
      display: flex;
      flex-direction: column;
      align-items: center;
      transition: width 0.3s;
    }

    .sidebar .profile {
      text-align: center;
      margin-bottom: 40px;
    }

    .sidebar .profile img {
      width: 100px;
      height: 100px;
      border-radius: 50%;
      margin-bottom: 15px;
      border: 3px solid #ffffff;
    }

    .sidebar .profile h2 {
      font-size: 1.2em;
      margin-bottom: 5px;
    }

    .sidebar .profile a {
      color: #ffffff;
      text-decoration: none;
      font-size: 1.1em;
      display: flex;
      align-items: center;
      justify-content: center;
      margin-top: 10px;
    }

    .sidebar .profile a i {
      margin-right: 8px;
    }

    /* 메인 콘텐츠 */
    .main-content {
      margin-left: 250px; /* 사이드바 너비와 동일 */
      width: calc(100% - 250px);
      display: flex;
      flex-direction: column;
      min-height: 100vh;
      background-color: #ffffff;
    }

    /* 네비게이션 바 */
    .navbar {
      background-color: #ffffff;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
      z-index: 1000;
      width: 100%;
      position: sticky;
      top: 0;
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
      display: flex;
      align-items: center;
    }

    .navbar-links a i {
      margin-right: 5px;
    }

    .navbar-links a:hover {
      color: #ff0000; /* 유튜브 레드 */
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
      margin-top: 0; /* 네비게이션 바 높이 제거 */
    }

    .banner h1 {
      font-size: 3em;
      text-align: center;
      color: #ffffff;
      padding: 20px;
      background: rgba(0, 0, 0, 0.5);
      border-radius: 10px;
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
      border: 1px solid #e0e0e0;
    }

    .card:hover {
      transform: translateY(-5px);
      box-shadow: 0 8px 12px rgba(0,0,0,0.2);
    }

    .card img {
      width: 100%;
      height: 180px;
      object-fit: cover;
      background-color: #f0f0f0;
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
      text-decoration: none;
    }

    .card-title:hover {
      color: #ff0000; /* 유튜브 레드 */
    }

    .card-description {
      flex: 1;
      color: #555555;
      margin-bottom: 15px;
      font-size: 0.95em;
    }

    .card-link {
      text-align: right;
    }

    .card-link a {
      display: inline-block;
      padding: 10px 15px;
      background-color: #ff0000; /* 유튜브 레드 */
      color: #ffffff;
      text-decoration: none;
      border-radius: 4px;
      transition: background-color 0.3s;
      font-weight: 500;
      font-size: 0.9em;
    }

    .card-link a:hover {
      background-color: #cc0000;
    }

    /* 커밋 로그 섹션 */
    .commits-section {
      padding: 20px;
      max-width: 1200px;
      margin: 0 auto;
    }

    .commits-section h2 {
      margin-bottom: 20px;
      color: #24292e;
      font-size: 2em;
      border-bottom: 2px solid #e0e0e0;
      padding-bottom: 10px;
    }

    .commit {
      background-color: #ffffff;
      border-radius: 8px;
      padding: 15px;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
      margin-bottom: 15px;
      display: flex;
      align-items: center;
      border-left: 4px solid #ff0000; /* 유튜브 레드 포인트 */
    }

    .commit .avatar {
      margin-right: 15px;
    }

    .commit .avatar img {
      width: 50px;
      height: 50px;
      border-radius: 50%;
      border: 2px solid #e0e0e0;
    }

    .commit .commit-info {
      flex: 1;
    }

    .commit .commit-info h4 {
      margin-bottom: 5px;
      color: #0366d6;
      font-size: 1em;
      cursor: pointer;
    }

    .commit .commit-info h4:hover {
      text-decoration: underline;
    }

    .commit .commit-info p {
      color: #555555;
      font-size: 0.9em;
      margin-bottom: 5px;
    }

    .commit .commit-date {
      color: #999999;
      font-size: 0.8em;
      white-space: nowrap;
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
      font-size: 0.9em;
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
    }

    @media (max-width: 768px) {
      .sidebar {
        width: 60px;
        padding: 10px;
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
      }

      .card img {
        height: 150px;
      }

      .commit .commit-info h4 {
        font-size: 0.9em;
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
          
          // 썸네일 이미지 설정 (프로젝트의 홈페이지나 README에 이미지가 있다면 사용)
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
                    <img src="${latestCommit.author ? latestCommit.author.avatar_url : 'https://via.placeholder.com/50'}" alt="Author Avatar">
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

    // 추가: 저장소 언어 및 스타 수 스타일링
    const style = document.createElement('style');
    style.innerHTML = `
      .card-info {
        display: flex;
        justify-content: flex-start;
        gap: 10px;
        margin-bottom: 15px;
      }
      .repo-language, .repo-stars {
        background-color: #f1f1f1;
        padding: 5px 10px;
        border-radius: 20px;
        font-size: 0.8em;
        display: flex;
        align-items: center;
      }
      .repo-stars i {
        margin-right: 5px;
        color: #ffcc00;
      }
    `;
    document.head.appendChild(style);
  </script>
</body>
</html>
