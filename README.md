# Portefolio - Développeur Back-End Python

Bonjour bienvenue sur mon Portefolio, je suis Assakali Mehdi , développeur junior spécialise en développement back-end avec python.

---

## Formation 

**Titre** : Développeur d'application Python
**Organisme**: Openclassrooms 
**Durée** : 12 mois
**Compétences acquise** : 
 - Concevoir des applications Python grâce au framework Django.
 - Maintenir et mettre à jour des applications existantes.
 - Intégrer des bases de données et des APIs.
 - Optimiser les performances des applications pour une expérience fluide.
 - Tester et déboguer des applications pour garantir leur bon fonctionnement.

## Compétences techniques

### 1. Manipulation de données
**Description**: Utilisation de bibliothèques Python pour extraire, traiter, et analyser des données.
**Exemple de code**:
    # importer les modules:
     import requests
     from bs4 import BeautifulSoup
     import csv

    # Envoyer une requête à la page web:
    base_url = 'http://books.toscrape.com'
    response = requests.get(base_url)

    # parser le contenu html:
    soup = BeautifulSoup(response.text, features="html.parser")
    liens_livres_html = soup.find('ol' , class_= 'row').findAll('h3')

    # stucturer les données dans Dataframe:
    with open (fichier_csv,'w',encoding='utf-8-sig', newline ='') as csvfile:

        writer = csv.writer(csvfile)

        writer.writerow(entete_produit)
        writer.writerows(tous_les_produits_categorie)

### 2. Gestion de base de données
**Description**: Ce projet montre ma matrise des concepts de gestion de base de données, associés à la programmation orienté objet. Il montre aussi un principe fondamental, la structure MVC (Modèle-vue-Controleur)
**Exemple de code**:
    # Création d'entité du programme en objet(Modèle):
        class Joueur:
        # Représente un joueur.
        def __init__(self, nom, prenom, date_de_naissance, id_nationale, score):
            self.nom = nom
            self.prenom = prenom
            self.date_de_naissance = date_de_naissance
            self.id_nationale = id_nationale
            self.score = score

    # Gestion des interactions(Controleur):
    def ajouter_joueur(self, nom, prenom, date_de_naissance, id_nationale):
        # Ajoute un joueur à la liste.
        self.gestion_joueurs.ajouter_joueur(nom, prenom, date_de_naissance, id_nationale, score=0)
    
    # Sauvegarde et chargement des données:
    class GestionDeBase:
        def __init__(self, dossier_data="data"):
            self.dossier_data = os.path.abspath(os.path.join(os.path.dirname(__file__), "..", dossier_data))
            if not os.path.exists(self.dossier_data):
                os.makedirs(self.dossier_data)

        def chemin_fichier(self, filename):
            return os.path.join(self.dossier_data, filename)

        def sauvegarder_fichier(self, filename, data):
            with open(self.chemin_fichier(filename), "w", encoding="utf-8") as f:
                json.dump(data, f, ensure_ascii=False, indent=4)

        def charger_fichier(self, filename):
            chemin_fichier = self.chemin_fichier(filename)
            if os.path.exists(chemin_fichier):
                with open(chemin_fichier, "r", encoding="utf-8") as f:
                    return json.load(f)
            return None


        class Gestion_information_joueur(GestionDeBase):
            def sauvegarder_joueurs(self, joueurs, filename="joueurs.json"):
                joueurs_existants = self.charger_joueurs(filename)
                joueurs_dict = {joueur.id_nationale: joueur for joueur in joueurs_existants}

                for joueur in joueurs:
                    joueurs_dict[joueur.id_nationale] = joueur

                listes_joueurs_dict = [
                    {
                        "nom": joueur.nom,
                        "prenom": joueur.prenom,
                        "date_de_naissance": joueur.date_de_naissance,
                        "id_nationale": joueur.id_nationale,
                        "score": joueur.score,
                    }
                    for joueur in joueurs_dict.values()
                ]
                self.sauvegarder_fichier(filename, listes_joueurs_dict)

    # Affichage des données

    def afficher_tournois(self):
        tournois = self.gestion_rapports.afficher_tournois()
        if not tournois:
            self.menu.afficher_message("Auncun tournoi disponible.")
            return
        for tournoi in tournois:
            self.menu.afficher_message(tournoi)

    def afficher_message(self, message):
        print(message)

### 3. Développement d'un Interface Utilisateur Web Dynamique
**Description**: Cette compétence illustre ma capacité à concevoir et développer une interface utilisateur web interactive et attrayante, en utilisant des technologies front-end modernes telles que HTML, CSS
                et Javascript. 
**Exemple de code**:
    Génération et manipulation dynamiquement à partir d'une API et les intégrer dans l'interface utilisateur.

            async function chargerFilmsParCategorie(categorie, containerSelector) {  
        
        const data = await fetchFilms(`${API_URL}?genre=${categorie}&sort_by=-imdb_score&page_size=6`);    
        const filmsContainer = document.querySelector(containerSelector);
        
        filmsContainer.innerHTML= "";    

        if (data && data.results && data.results.length > 0){
            const detailsArray = await Promise.all(data.results.map(film => fetchFilms(film.url)))

            detailsArray.forEach(details =>  {           
                if (details){            
                    const filmElement = document.createElement("div");
                    filmElement.classList.add("fiche-de-film");          
                    
                
                    
                    filmElement.innerHTML =` 
                        <img src="${details.image_url}" alt="Affcihe de ${details.title}" class="image-film"
                        onerror="this.onerror=null; this.src='${IMAGE_PAR_DEFAUT}';">
                        <div class="overlay">
                            <h3 class="titre-film">${details.title}</h3>
                            <button class="film-boutton">Détails</button>
                        </div>
                    `;
                    filmsContainer.appendChild(filmElement);
                    console.clear()
                    filmElement.querySelector(".film-boutton").addEventListener('click', () => {
                        ouvrirModale(details);
                    });
                }
            });

        }  else {
            console.warn("Aucun film trouvé ou l'API est désactivé")
        }   
        
            
    }

    # Structure de la fenêtre modale pour les details d'un film

     <div class="modale" id="modale">    
        <div class="modale-contenu">            
            <div class="modale-haut">                
                <h2 class="modale-titre">Titre du film</h2>
                <p class="modale-info">
                    Année - Genres<br>
                    Classification - Durée (Pays)<br>
                    IMDB score : 8.1/10
                </p>            
                <p class="modale-réalisateur"><strong>Réalisé par:</strong><br> Nom du réalisateur</p>  
                <button class="modale-fermer">&times;</button>              
            </div>
                <div class="modale-description">                    
                        <p class="modale-résumé">Lorem ipsum odor amet, consectetuer adipiscing elit. Etiam dis massa ad himenaeos sapien efficitur mus. Erat facilisis habitant erat curabitur viverra. Curae mauris facilisis vivamus nisi, erat ultrices quam. Aaugue justo elit phasellus dolor. Penatibus vulputate efficitur auctor, cursus taciti parturient aliquet. Proin vehicula rhoncus mus iaculis fermentum fermentum nisi sit.</p>
                        
                </div>
                <div class="modale-image">
                    <img src="https://fastly.picsum.photos/id/273/200/300.jpg?hmac=C0IK2DPqr03oiShSklDGIHBzHorcmVrky7A_uvBEzIM" alt="Affcihe-du-film">
                </div>
                <div class="modale-acteurs">
                    <p>
                        <strong>Avec:</strong><br> Lorem ipsum odor amet, consectetuer adipiscing elit. Habitant accumsan aliquam sagittis amet sollicitudin magna massa pretium. Mollis mattis lectus vel molestie morbi nostra dui massa feugiat.
                    </p>
                </div>
                <button class="modale-boutton">Fermer</button>             
        </div>
    </div>

    # disposition de la grille de film ainsi que son overlay pour plus de design

        .film-grille{
        display: grid;
        grid-template-columns: 1fr;    
        gap: 20px; 
    }

        .overlay {
        position: absolute;
        top: 40px;     
        width: 329px;
        height: 40%;
        background: rgba(0, 0, 0, 0.5);
        color: #FFFFFF;
        display: flex;
        flex-direction: column;    
        align-items: center;
        justify-content: space-between;
        padding: 10px;    
        
    }

### 4. [Langage et technologie]
**Langage de programation**:  
    - Python : Langage principale utilisé pour le développement back-end et la manipulation des données.
    - HTML : Création de la structure sémantique des pages web.
    - CSS: Mise en page, design responsive et amélioration visuelle des interfaces.

**Framework et Bibliothèque**
    - Django: Développement web back-end avec un structure robuste et sécurisée.
    - Json: Format utilisé pour l'échange et le stockage de données structurés.

**Outils de développement**
    - Git & Github: Gestion de versions et collaboration sur des projets via des dépôts.
    - VsCode: Environement de développement intégré pour écrire, tester et déboguer le code.

## Me contacter

Si vous souhaitez me contacter ou en savoir plus sur mes projets, n'hésiter pas à me joindre :

-**Email**: assakali.mehdi@gmail.com
-**Linkdin**: Mehdi assakali
-**Github** : Medspyas ; https://github.com/Medspyas




    
    

   
