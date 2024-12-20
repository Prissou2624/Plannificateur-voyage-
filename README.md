<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Planificateur de Voyage Numérique</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <style>
        body {
            background-color: #f4f8fc;
            color: #333;
            margin: 20px;
        }
        .hidden {
            display: none;
        }
        .page {
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 10px;
            margin-bottom: 20px;
            background-color: #fff;
        }
        .navigation {
            text-align: center;
            margin-top: 20px;
        }
        .btn-nav {
            margin: 0 10px;
        }
        .confirmation {
            display: none;
            background-color: #dff0d8;
            color: #3c763d;
            padding: 15px;
            border-radius: 5px;
            margin-top: 20px;
            text-align: center;
        }
        .error {
            color: red;
            margin-top: -15px;
            margin-bottom: 15px;
            font-size: 12px;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Page d'accueil -->
        <div id="homePage" class="page">
            <h1 class="text-center">Planificateur de Voyage Numérique</h1>
            <div class="text-center">
                <img src="https://via.placeholder.com/400x200" alt="Illustration de voyage" class="img-fluid mt-4 mb-4">
            </div>
            <p class="text-center">
                Bienvenue dans le planificateur qui vous aide à organiser vos voyages facilement et efficacement.
            </p>
            <div class="text-center">
                <button id="startButton" class="btn btn-primary">Commencer</button>
            </div>
        </div>

        <!-- Section de connexion avec code d'accès -->
        <div id="loginSection" class="page hidden">
            <h3>Entrez votre code d'accès</h3>
            <form id="accessForm">
                <input type="text" id="accessCode" placeholder="Code d'accès" required class="form-control">
                <button type="submit" class="btn btn-primary mt-2">Valider</button>
            </form>
            <p id="errorMessage" style="color: red; display: none;">Code d'accès invalide.</p>
        </div>

        <!-- Section du planificateur -->
        <div id="plannerSection" class="page hidden">
            <h2>Planifiez votre Voyage</h2>
            <form id="voyageForm">
                <div class="form-group">
                    <label for="destination">Destination :</label>
                    <input type="text" class="form-control" id="destination" name="destination" required>
                </div>
                <div class="form-group">
                    <label for="date-depart">Date de départ :</label>
                    <input type="date" class="form-control" id="date-depart" name="date-depart" required>
                </div>
                <div class="form-group">
                    <label for="date-retour">Date de retour :</label>
                    <input type="date" class="form-control" id="date-retour" name="date-retour" required>
                </div>
                <div class="form-group">
                    <label for="nombre-passagers">Nombre de passagers :</label>
                    <select class="form-control" id="nombre-passagers" name="nombre-passagers" required>
                        <option value="" disabled selected>Choisissez...</option>
                        <option value="1">1</option>
                        <option value="2">2</option>
                        <option value="3">3</option>
                        <option value="4">4</option>
                        <option value="5">5+</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="type-hebergement">Type d'hébergement :</label>
                    <select class="form-control" id="type-hebergement" name="type-hebergement" required>
                        <option value="" disabled selected>Choisissez...</option>
                        <option value="hotel">Hôtel</option>
                        <option value="auberge">Auberge</option>
                        <option value="appartement">Appartement</option>
                        <option value="camping">Camping</option>
                    </select>
                </div>
                <p id="costPreview">Coût estimé : 0€</p>
                <button type="submit" class="btn btn-success">Planifier le Voyage</button>
            </form>
        </div>

        <div class="navigation">
            <button class="btn btn-secondary btn-nav hidden" id="prevPage">Précédent</button>
            <button class="btn btn-primary btn-nav hidden" id="nextPage">Suivant</button>
        </div>
    </div>

    <script>
        // Gestion de la navigation entre pages
        const pages = document.querySelectorAll('.page');
        let currentPage = 0;

        document.getElementById('startButton').addEventListener('click', () => {
            pages[currentPage].classList.add('hidden');
            currentPage++;
            pages[currentPage].classList.remove('hidden');
            toggleButtons();
        });

        document.getElementById('prevPage').addEventListener('click', () => {
            pages[currentPage].classList.add('hidden');
            currentPage--;
            pages[currentPage].classList.remove('hidden');
            toggleButtons();
        });

        document.getElementById('nextPage').addEventListener('click', () => {
            pages[currentPage].classList.add('hidden');
            currentPage++;
            pages[currentPage].classList.remove('hidden');
            toggleButtons();
        });

        function toggleButtons() {
            document.getElementById('prevPage').classList.toggle('hidden', currentPage === 0);
            document.getElementById('nextPage').classList.toggle('hidden', currentPage === pages.length - 1);
        }

        // Vérification du code d'accès
        document.getElementById('accessForm').addEventListener('submit', (event) => {
            event.preventDefault();
            const code = document.getElementById('accessCode').value;

            // Appeler un backend fictif pour valider le code d'accès
            if (code === "1234") { // Exemple de code d'accès valide
                alert("Code d'accès validé!");
                document.getElementById('loginSection').classList.add('hidden');
                currentPage++;
                pages[currentPage].classList.remove('hidden');
                toggleButtons();
            } else {
                document.getElementById('errorMessage').style.display = 'block';
            }
        });
    </script>
</body>
</html>
"""
