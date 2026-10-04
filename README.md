#hospital 1
<!DOCTYPE html>
<html lang="da">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Hospital Portal</title>

  <link rel="stylesheet" href="style.css">
</head>

<body>

  <!-- LOGIN -->
  <div id="login" class="login-screen">
    <div class="login-card">

      <div class="logo">✚</div>

      <p class="eyebrow">MEDICINSK AFDELING</p>

      <h1>Hospital Portal</h1>

      <p class="muted">
        Administrér fiktive RP-rapporter, personale og læge-ID'er.
      </p>

      <button class="discord-btn" onclick="login()">
        🔵 Log ind med Discord
      </button>

      <p class="demo">
        Demo-login – Discord OAuth kan tilkobles senere.
      </p>

    </div>
  </div>


  <!-- HOVEDAPP -->
  <div id="app" class="app hidden">

    <!-- SIDEBAR -->
    <aside class="sidebar">

      <div class="brand">
        <div class="brand-icon">✚</div>

        <div>
          <b>Hospital</b>
          <small>Medicinsk Afdeling</small>
        </div>
      </div>


      <nav>

        <button class="nav active" onclick="showPage('dashboard', this)">
          🏠 <span>Dashboard</span>
        </button>

        <button class="nav" onclick="showPage('reports', this)">
          📋 <span>Rapporter</span>
        </button>

        <button class="nav" onclick="showPage('new-report', this)">
          ➕ <span>Ny rapport</span>
        </button>

        <button class="nav" onclick="showPage('staff', this)">
          👨‍⚕️ <span>Personale</span>
        </button>

        <button class="nav" onclick="showPage('handbook', this)">
          📕 <span>Lægehåndbog</span>
        </button>

      </nav>


      <div class="sidebar-user">

        <div class="user-row">

          <div class="avatar">
            DJ
          </div>

          <div>
            <b>Dr. Jensen</b>
            <small>LÆGE-247 · Læge</small>
          </div>

        </div>

        <button class="logout" onclick="logout()">
          Log ud
        </button>

      </div>

    </aside>


    <!-- MAIN -->
    <main class="main">

      <!-- TOPBAR -->
      <header class="topbar">

        <div>
          <span class="status-dot"></span>
          Hospitalssystem online
        </div>

        <div id="clock"></div>

      </header>


      <!-- DASHBOARD -->
      <section id="dashboard" class="page">

        <div class="page-header">

          <div>

            <p class="eyebrow">
              OVERSIGT
            </p>

            <h2>
              God aften, Dr. Jensen 👋
            </h2>

            <p class="muted">
              Her er status for den medicinske afdeling.
            </p>

          </div>

          <button
            class="primary"
            onclick="showPage('new-report')">

            ＋ Ny rapport

          </button>

        </div>


        <!-- STATISTIK -->
        <div class="stats">

          <div class="stat">

            <div class="stat-icon blue">
              📋
            </div>

            <div>

              <small>Rapporter</small>

              <strong id="reportCount">
                0
              </strong>

            </div>

          </div>


          <div class="stat">

            <div class="stat-icon green">
              ✓
            </div>

            <div>

              <small>Status</small>

              <strong>
                På vagt
              </strong>

            </div>

          </div>


          <div class="stat">

            <div class="stat-icon purple">
              👨‍⚕️
            </div>

            <div>

              <small>Rang</small>

              <strong>
                Læge
              </strong>

            </div>

          </div>


          <div class="stat">

            <div class="stat-icon orange">
              #
            </div>

            <div>

              <small>Læge-ID</small>

              <strong>
                LÆGE-247
              </strong>

            </div>

          </div>

        </div>


        <!-- DASHBOARD CARDS -->
        <div class="grid-2">


          <!-- SENESTE RAPPORTER -->
          <div class="card">

            <div class="card-header">

              <h3>
                Seneste rapporter
              </h3>

              <button
                class="link"
                onclick="showPage('reports')">

                Se alle

              </button>

            </div>

            <div id="recentReports"></div>

          </div>


          <!-- NUMRE -->
          <div class="card">

            <h3>
              📞 Vigtige numre
            </h3>


            <div class="contact">

              <span>🚑</span>

              <div>
                <b>Akut</b>
                <small>112</small>
              </div>

            </div>


            <div class="contact">

              <span>🏥</span>

              <div>
                <b>Hospital</b>
                <small>+45 12 34 56 78</small>
              </div>

            </div>


            <div class="contact">

              <span>👑</span>

              <div>
                <b>Ledelse</b>
                <small>+45 87 65 43 21</small>
              </div>

            </div>

          </div>

        </div>

      </section>


      <!-- RAPPORTER -->
      <section id="reports" class="page hidden">

        <div class="page-header">

          <div>

            <p class="eyebrow">
              DOKUMENTATION
            </p>

            <h2>
              Rapporter
            </h2>

            <p class="muted">
              Oversigt over hospitalets RP-rapporter.
            </p>

          </div>

          <button
            class="primary"
            onclick="showPage('new-report')">

            ＋ Ny rapport

          </button>

        </div>


        <div class="card">

          <div class="filters">

            <input
              id="search"
              type="text"
              placeholder="Søg efter patient eller ID..."
              oninput="renderReports()">


            <select
              id="typeFilter"
              onchange="renderReports()">

              <option value="">
                Alle typer
              </option>

              <option value="Patient">
                Patient
              </option>

              <option value="Akut">
                Akut
              </option>

              <option value="Indlæggelse">
                Indlæggelse
              </option>

              <option value="Udskrivelse">
                Udskrivelse
              </option>

            </select>

          </div>


          <div id="allReports"></div>

        </div>

      </section>


      <!-- NY RAPPORT -->
      <section id="new-report" class="page hidden">

        <div class="page-header">

          <div>

            <p class="eyebrow">
              DOKUMENTATION
            </p>

            <h2>
              Ny rapport
            </h2>

            <p class="muted">
              Opret en ny fiktiv RP-patientrapport.
            </p>

          </div>

        </div>


        <form
          id="reportForm"
          class="card form">


          <div class="form-grid">


            <label>

              Patientnavn

              <input
                name="patient"
                required
                placeholder="Fx Peter Hansen">

            </label>


            <label>

              Patient-ID

              <input
                name="patientId"
                placeholder="Fx PAT-4821">

            </label>


            <label>

              Rapporttype

              <select name="type">

                <option>
                  Patient
                </option>

                <option>
                  Akut
                </option>

                <option>
                  Indlæggelse
                </option>

                <option>
                  Udskrivelse
                </option>

              </select>

            </label>


            <label>

              Status

              <select name="status">

                <option>
                  🟢 Udskrevet
                </option>

                <option>
                  🟠 Indlagt
                </option>

                <option>
                  🔵 Observation
                </option>

                <option>
                  🟣 Overført
                </option>

              </select>

            </label>


          </div>


          <label>

            Symptomer

            <textarea
              name="symptoms"
              required
              placeholder="Beskriv symptomer...">
            </textarea>

          </label>


          <label>

            Undersøgelse

            <textarea
              name="exam"
              required
              placeholder="Beskriv undersøgelsen...">
            </textarea>

          </label>


          <label>

            Behandling

            <textarea
              name="treatment"
              placeholder="Beskriv behandling...">
            </textarea>

          </label>


          <label>

            Bemærkninger

            <textarea
              name="notes"
              placeholder="Eventuelle bemærkninger...">
            </textarea>

          </label>


          <div class="form-footer">

            <span class="muted">

              Behandler:
              <b>LÆGE-247</b>

            </span>


            <button
              class="primary"
              type="submit">

              Gem rapport

            </button>

          </div>

        </form>

      </section>


      <!-- PERSONALE -->
      <section id="staff" class="page hidden">

        <div class="page-header">

          <div>

            <p class="eyebrow">
              ADMINISTRATION
            </p>

            <h2>
              Personale
            </h2>

            <p class="muted">
              Oversigt over hospitalets medarbejdere.
            </p>

          </div>

          <button
            class="primary"
            onclick="alert('Medarbejder-oprettelse kommer i den fulde version.')">

            ＋ Tilføj medarbejder

          </button>

        </div>


        <div class="card">

          <table>

            <thead>

              <tr>

                <th>
                  Medarbejder
                </th>

                <th>
                  Læge-ID
                </th>

                <th>
                  Rang
                </th>

                <th>
                  Status
                </th>

              </tr>

            </thead>


            <tbody>

              <tr>

                <td>
                  <b>Dr. Jensen</b>
                </td>

                <td>
                  LÆGE-247
                </td>

                <td>
                  🩺 Læge
                </td>

                <td>
                  <span class="badge green">
                    Aktiv
                  </span>
                </td>

              </tr>


              <tr>

                <td>
                  <b>Dr. Nielsen</b>
                </td>

                <td>
                  LÆGE-103
                </td>

                <td>
                  🔷 Overlæge
                </td>

                <td>
                  <span class="badge green">
                    Aktiv
                  </span>
                </td>

              </tr>


              <tr>

                <td>
                  <b>Anna Larsen</b>
                </td>

                <td>
                  LÆGE-315
                </td>

                <td>
                  🩹 Sygeplejerske
                </td>

                <td>
                  <span class="badge orange">
                    Fri
                  </span>
                </td>

              </tr>

            </tbody>

          </table>

        </div>

      </section>


      <!-- LÆGEHÅNDBOG -->
      <section id="handbook" class="page hidden">

        <div class="page-header">

          <div>

            <p class="eyebrow">
              REFERENCE
            </p>

            <h2>
              Lægehåndbog
            </h2>

            <p class="muted">
              Regler og procedurer for hospitalets RP.
            </p>

          </div>

        </div>


        <div class="handbook">


          <div class="card">

            <h3>
              👑 Rangsystem
            </h3>

            <p>
              Direktør → Medicinsk chef →
              Overlæge → Speciallæge →
              Læge → Sygeplejerske →
              Studerende → Praktikant.
            </p>

          </div>


          <div class="card">

            <h3>
              🆔 Læge-ID
            </h3>

            <p>
              Alle medarbejdere får et unikt ID
              fra <b>LÆGE-001</b> til
              <b>LÆGE-999</b>.
            </p>

          </div>


          <div class="card">

            <h3>
              📋 Rapportregler
            </h3>

            <ul>

              <li>
                Alle RP-behandlinger dokumenteres.
              </li>

              <li>
                Brug altid medarbejder-ID.
              </li>

              <li>
                Hold rapporter tydelige og saglige.
              </li>

              <li>
                Brug kun fiktive RP-oplysninger.
              </li>

            </ul>

          </div>


        </div>

      </section>

    </main>

  </div>


<script src="app.js"></script>

</body>
</html>