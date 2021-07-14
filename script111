function singnup() {
    var nom = document.getElementById("nom").value;
    if (nom.length != 0) {
        document.getElementById("nomError").innerHTML = "";
    } else {
        document.getElementById("nomError").innerHTML = "Nom Obligatoire";
        document.getElementById("nomError").style.color = "red";
    }

    var immatriculeFiscale = document.getElementById("immatriculeFiscale").value;
    if (immatriculeFiscale.length != 0) {
        document.getElementById("immatriculeFiscaleError").innerHTML = "";
    } else {
        document.getElementById("immatriculeFiscaleError").innerHTML = "immatriculeFiscale Obligatoire";
        document.getElementById("immatriculeFiscaleError").style.color = "red";
    }

    var adresse = document.getElementById("adresse").value;
    if (adresse.length != 0) {
        document.getElementById("adresseError").innerHTML = "";
    } else {
        document.getElementById("adresseError").innerHTML = "adresse Obligatoire";
        document.getElementById("adresseError").style.color = "red";
    }

    var ca = document.getElementById("ca").value;
    if (ca > 0) {
        document.getElementById("caError").innerHTML = "";
    } else {
        document.getElementById("caError").innerHTML = "Chiffre d'affaire doit etre positive";
        document.getElementById("caError").style.color = "red";
    }

    var forme = document.getElementById("forme").value;
    if (forme.length != "") {
        document.getElementById("formeError").innerHTML = "";
    } else {
        document.getElementById("formeError").innerHTML = "Forme Obligatoire";
        document.getElementById("formeError").style.color = "red";
    }

    var activite = document.getElementById("activite").value;
    if (activite.length != 0) {
        document.getElementById("activiteError").innerHTML = "";
    } else {
        document.getElementById("activiteError").innerHTML = "activite Obligatoire";
        document.getElementById("activiteError").style.color = "red";
    }

    var tel = document.getElementById("tel").value;
    if (tel.length == 8) {
        document.getElementById("telError").innerHTML = "";
    } else {
        document.getElementById("telError").innerHTML = "tel doit etre de 8 chiffres";
        document.getElementById("telError").style.color = "red";
    }

    var email = document.getElementById("email").value;
    var verifEmail = validateEmail(email);
    if (verifEmail) {
        document.getElementById("emailError").innerHTML = "";
    } else {
        document.getElementById("emailError").innerHTML = "email Obligatoire";
        document.getElementById("emailError").style.color = "red";
    }

    var pwd = document.getElementById("pwd").value;
    if (pwd.length >= 8) {
        document.getElementById("pwdError").innerHTML = "";
    } else {
        document.getElementById("pwdError").innerHTML = "pwd doit avoir au minimum 8 caracteres";
        document.getElementById("pwdError").style.color = "red";
    }

    var confirmPwd = document.getElementById("confirmPwd").value;
    if (confirmPwd == pwd) {
        document.getElementById("confirmPwdError").innerHTML = "";
    } else {
        document.getElementById("confirmPwdError").innerHTML = "confirmPwd doit etre conforme de password";
        document.getElementById("confirmPwdError").style.color = "red";
    }

    if ((nom.length != 0) && (immatriculeFiscale.length != 0) && (adresse.length != 0) && (ca > 0) && (forme.length != 0)
        && (activite.length != 0) && (tel.length == 8) && (verifEmail) && (pwd.length >= 8) && (confirmPwd == pwd)) {
        var utilisateurs = JSON.parse(localStorage.getItem("utilisateurs") || "[]");
        var idUtilisateur = JSON.parse(localStorage.getItem("idUtilisateur") || "2");
        var utilisateur = {
            id: idUtilisateur,
            nom: nom,
            immatriculeFiscale: immatriculeFiscale,
            adresse: adresse,
            ca: ca,
            forme: forme,
            activite: activite,
            tel: tel,
            email: email,
            pwd: pwd,
            confirmPwd: confirmPwd,
            role: "entreprise"
        };
        utilisateurs.push(utilisateur);

        localStorage.setItem("utilisateurs", JSON.stringify(utilisateurs));
        localStorage.setItem("idUtilisateur", idUtilisateur + 1);

        Swal.fire({
            position: 'top-end',
            icon: 'success',
            title: 'votre Compte a ete creer',
            showConfirmButton: false,
            timer: 3000,
        })

        location.replace("login.html");

    }
}

function validateEmail(email) {
    const regExp = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
    return regExp.test(String(email).toLowerCase());
}

function login() {
    var email = document.getElementById('email').value;
    var pwd = document.getElementById('pwd').value;

    var utilisateurs = JSON.parse(localStorage.getItem("utilisateurs") || "[]");

    // verification si l'email et le mot de passe existent ou pas 
    for (let i = 0; i < utilisateurs.length; i++) {
        if ((utilisateurs[i].email == email) && (utilisateurs[i].pwd == pwd)) {
            var findUtilisateur = utilisateurs[i];
        }
    }

    switch (findUtilisateur.role) {
        case "admin" :
            localStorage.setItem("utilisateurConnecte", JSON.stringify(findUtilisateur));
            location.replace("admin.html");
        break;
        case "entreprise" :
            localStorage.setItem("utilisateurConnecte", JSON.stringify(findUtilisateur));
            location.replace("entreprise2.html");
        break;

        default:
        break;
    }
}


function addAdmin() {
    var utilisateurs = JSON.parse(localStorage.getItem("utilisateurs") || "[]");

    var admin =  { 
        id:1,
        nom: "Bouazizi",
        prenom:"Med Amine",
        email:"Amine.Bouazizi@gmail.com",
        pwd: "0000",
        role:"admin"
    };

    utilisateurs.push(admin);

    localStorage.setItem("utilisateurs",JSON.stringify(utilisateurs));
    localStorage.setItem("adminAjouter", "true");
}

function AddElement(event) {
    event.preventDefault();

    IdElement = document.getElementById("plat");

    console.log(IdElement.value);

    let ligne = document.createElement('tr');
    let cellule = document.createElement('td');

    cellule.innerHTML=IdElement.value;
    ligne.appendChild(cellule);

    let IdTableau = document.getElementById('body');

    IdTableau.appendChild(ligne);

}

function ajoutCategorie() {
    var nomCategorie = document.getElementById("nomCategorie").value;
    var verifNomCategorie = verifLength(nomCategorie,4);
    if (verifNomCategorie) {
        document.getElementById("nomCategorieError").innerHTML='';
    }
    else{
        document.getElementById("nomCategorieError").innerHTML='Le nom de la categorie doit comporter au moins 4 lettres';
        document.getElementById("nomCategorieError").style.color='red';
    }
    var descriptionCategorie = document.getElementById("descriptionCategorie").value;
    if (descriptionCategorie != "") {
        document.getElementById("descriptionCategorieError").innerHTML='';
    }
        
else{
    document.getElementById("descriptionCategorieError").innerHTML='La description doit être non vide';
    document.getElementById("descriptionCategorieError").style.color='red';
}

if (verifNomCategorie && (descriptionCategorie != "")) {
    var categories = JSON.parse(localStorage.getItem("categories") || "[]");
    var idCategorie = JSON.parse(localStorage.getItem("idCategorie") || "1");
    var utilisateurConnecte = JSON.parse(localStorage.getItem("utilisateurConnecte"));
    var categorie ={
        id: idCategorie,
        nom : nomCategorie,
        idEntreprise : utilisateurConnecte.id,
        descriptionCategorie : descriptionCategorie
    };
    categories.push(categorie);
    localStorage.setItem("categories", JSON.stringify(categories));
    localStorage.setItem("idCategorie",idCategorie + 1);
    location.reload();
}

}

function verifLength(ch,nb) {
return ch.length >= nb ;
}

function displayCategories() {
     var categories = JSON.parse(localStorage.getItem("categories") || "[]");

    var categoryTable = `` ;
    var utilisateurConnecte = JSON.parse(localStorage.getItem("utilisateurConnecte"));
    var categoriesEntreprise = [];

    for (let i = 0; i < categories.length; i++) {
        if (utilisateurConnecte.id == categories[i].idEntreprise) {
            categoriesEntreprise.push(categories[i]) ;
        }
    }

    categoryTable = `<table class="table table-dark table-hover">
        <tr>
            <th> Nom</th>
            <th> Description</th>
            <th> Actions</th>

        </tr>`;

   for (let i = 0; i < categoriesEntreprise.length; i++) {
    categoryTable = categoryTable + `
    <tr>
    <td> ${categoriesEntreprise[i].nom}</td>
    <td> ${categoriesEntreprise[i].descriptionCategorie}</td>
    <td> <button type="button" class="btn btn-warning" onclick="modifierCategorie(${categoriesEntreprise[i].id})">Modifier</button>
         <button type="button" class="btn btn-danger" onclick="supprimerObjet(${searchPosition(categoriesEntreprise[i].id,'categories')},'categories')">Supprimer</button>
    </td> 
    </tr>`;
   }
   categoryTable = categoryTable + `</table>` ;
    document.getElementById("categoryTable").innerHTML= categoryTable ;

}

function searchPosition(id,T) {
    var tab=JSON.parse(localStorage.getItem(T)||"[]");
    var pos;
    for (let i = 0; i < tab.length; i++) {
       
        if (tab[i].id==id) {
            pos=i;
            
        }
        
    }
return pos;
    
}


function supprimerObjet(pos,T) {
    var tab=JSON.parse(localStorage.getItem(T)|| "[]");
    tab.splice(pos,1);
    localStorage.setItem(T,JSON.stringify(tab));
    location.reload();
    
}

function modifierCategorie(id) {
    var categorie =RechercherObjet(id,"categories");
    console.log(categorie.descriptionCategorie);
    var ModifCategorie=`
    <div class="mb-3">
                            
    <input type="text" class="form-control" id="newNomCategorie"  value=${categorie.nom}> 
        <span id="newNomCategorieError"></span>
</div>
<div class="mb-3">
    <textarea class="form-control" id="newDescriptionCategorie" rows="3">${categorie.descriptionCategorie}</textarea>
    <span id="newDescriptionCategorieError"></span>

</div>
<button type="button" class="btn btn-primary" style="margin-left: 40%;" onclick="validerModifCategorie(${categorie.id})">Modifier</button>
    `;
    document.getElementById("ModifCategorie").innerHTML=ModifCategorie;
    
}

function RechercherObjet(id,T) {
    var objets =JSON.parse(localStorage.getItem(T)||"[]");
    for (let i = 0; i < objets.length; i++) {
        var obj;
        if (objets[i].id == id) {
            obj = objets[i];
        }
        
    }return obj;
    
}

function validerModifCategorie(id) {
    var newNomCategorie = document.getElementById("newNomCategorie").value;
    var verifNewNomCategorie = verifLength(newNomCategorie,4);
    if (verifNewNomCategorie) {
        document.getElementById("newNomCategorieError").innerHTML='';
    }
    else{
        document.getElementById("newNomCategorieError").innerHTML='Le nouveau nom de la categorie doit comporter au moins 4 lettres';
        document.getElementById("newNomCategorieError").style.color='red';
    }
    
    var newDescriptionCategorie = document.getElementById("newDescriptionCategorie").value;
    if (newDescriptionCategorie != "") {
        document.getElementById("newDescriptionCategorieError").innerHTML='';
    }
        
else{
    document.getElementById("newDescriptionCategorieError").innerHTML='La nouvell description doit être non vide';
    document.getElementById("newDescriptionCategorieError").style.color='red';
}

if (verifNewNomCategorie && (newDescriptionCategorie != "")) {
    var categories = JSON.parse(localStorage.getItem("categories") || "[]");
    for (let i = 0; i < categories.length; i++) {
        if (categories[i].id == id) {
            categories[i].nom = newNomCategorie;
            categories[i].descriptionCategorie = newDescriptionCategorie ;
        }
    }
    localStorage.setItem("categories",JSON.stringify(categories));
    location.reload();
}

}

// function ajoutProduit() {
//     var nomProduit = document.getElementById("nomProduit").value;
//     if (nomProduit != "") {
//         document.getElementById("nomProduitError").innerHTML="";
//     }
//     else{
//         document.getElementById("nomProduitError").innerHTML="Le nom du produit doit être non vide";
//         document.getElementById("nomProduitError").style.color='red' ;
//     }
//     var reference = document.getElementById("reference").value;
//     if (reference != "") {
//         document.getElementById("referenceError").innerHTML="";
//     }
//     else{
//         document.getElementById("referenceError").innerHTML="La référence doit être non vide";
//         document.getElementById("referenceError").style.color='red' ;
//     }
//     var prixAchat = document.getElementById("prixAchat").value;
//     if (prixAchat > 0) {
//         document.getElementById("prixAchatError").innerHTML="";
//     }
//     else{
//         document.getElementById("prixAchatError").innerHTML="Le prix d'achat doit être supérieur à zéro";
//         document.getElementById("prixAchatError").style.color='red' ;
//     }
//     var prixVente = document.getElementById("prixVente").value;
//     if (prixVente > 0) {
//         document.getElementById("prixVenteError").innerHTML="";
//     }
//     else{
//         document.getElementById("prixVenteError").innerHTML="Le prix de vente doit être supérieur à zéro";
//         document.getElementById("prixVenteError").style.color='red' ;
//     }
//     var stock = document.getElementById("stock").value;
//     if (stock > 0) {
//         document.getElementById("StockError").innerHTML="";
//     }
//     else{
//         document.getElementById("StockError").innerHTML="Le stock doit être supérieur à zéro";
//         document.getElementById("StockError").style.color='red' ;
//     }
//     var nomCategorie = document.getElementById("nomCategoriee").value;
//     var verifNomCategorie = verifLength(nomCategorie,4);
//     if (verifNomCategorie) {
//         document.getElementById("nomCategorieeError").innerHTML="";
//     }
//     else{
//         document.getElementById("nomCategorieeError").innerHTML="Le nom de la categorie doit comporter au moins 4 lettres";
//         document.getElementById("nomCategorieeError").style.color="red";
//     }

// if ((nomProduit != "") && (reference != "") && (prixAchat > 0) && (prixVente > 0) && (stock > 0) && verifNomCategorie) {
//     var produits = JSON.parse(localStorage.getItem("produits") || "[]");
//     var idProduit = JSON.parse(localStorage.getItem("idProduit") || "1");
//     var categories = JSON.parse(localStorage.getItem("categories") || "[]");
//     var utilisateurConnecte = JSON.parse(localStorage.getItem("utilisateurConnecte"));
//     var idCategorie = 0 ;

//     for (let i = 0; i < categories.length; i++) {
//         if ((categories[i].idEntreprise == utilisateurConnecte.id) && (categories[i].nom == nomCategorie)) {
//             idCategorie = categories[i].id ;
//         }
//     }

//     var produit = {
//         id: idProduit,
//         nom: nomProduit,
//         reference: reference,
//         prixAchat: prixAchat,
//         prixVente: prixVente,
//         stock: stock,
//         idEntreprise: utilisateurConnecte.id,
//         idCategorie: idCategorie
//     };
//     produits.push(produit);
//     localStorage.setItem("produits", JSON.stringify(produits));
//     localStorage.setItem("idProduit", idProduit + 1);
//     location.reload();
// }   
// }


function ajoutProduit() {
    var categories = JSON.parse(localStorage.getItem("categories") || "[]");
    var utilisateurConnecte = JSON.parse(localStorage.getItem("utilisateurConnecte"));
    var T = [] ;
    for (let i = 0; i < categories.length; i++) {
        if (categories[i].idEntreprise == utilisateurConnecte.id) {
            T.push(categories[i]) ;
        }
    }
    var produitForm = ``;
                        produitForm  = produitForm + `<div class="mb-3">
                            <input type="text" class="form-control" id="nomProduit" placeholder="Nom du Produit"> 
                                <span id="nomProduitError"></span>
                        </div>
                        <div class="mb-3">
                            <input type="text" class="form-control" id="reference" placeholder="Référence du Produit"> 
                                <span id="referenceError"></span>
                        </div>
                        <div class="mb-3">
                            <input type="number" class="form-control" id="prixAchat" placeholder="Prix d'achat du Produit"> 
                                <span id="prixAchatError"></span>
                        </div>
                        <div class="mb-3">
                            <input type="number" class="form-control" id="prixVente" placeholder="Prix de Vente du Produit"> 
                                <span id="prixVenteError"></span>
                        </div>
                        <div class="mb-3">
                            <input type="number" class="form-control" id="stock" placeholder="Stock du Produit"> 
                                <span id="stockError"></span>
                        </div>

                        <div class="mb-3">
                        <select class="form-select" aria-label="Default select example" id="selectionPrCategorie">
                            <option selected value="">choisir la catégorie</option>` ;

                        for (let i = 0; i < T.length; i++) {
                            produitForm = produitForm + `<option value=${T[i].id}>${T[i].nom}</option>`;
                        }   
                           
                        produitForm = produitForm + `</select>  
                        <span id="categorieSelectionneError"></span>
                        </div>
                        <button type="button" class="btn btn-primary" style="margin-left: 40%;" onclick="validerAjoutProduit()">Ajouter</button>`;

    document.getElementById("produitForm").innerHTML= produitForm ;

}

function validerAjoutProduit() {
    var nomProduit=document.getElementById("nomProduit").value;
    if (verifLength(nomProduit,4)) {
        document.getElementById("nomProduitError").innerHTML='';
    }
    else{
        document.getElementById("nomProduitError").innerHTML='Le nom du produit doit comporter au moins 4 lettres';
        document.getElementById("nomProduitError").style.color='red';
    }

    var reference =document.getElementById("reference").value;

    if (reference.length==6) {
        document.getElementById("referenceError").innerHTML='';
    }
    else{
        document.getElementById("referenceError").innerHTML='La reference doit comporter 6 caracteres';
        document.getElementById("referenceError").style.color='red';
    }


    var prixAchat=document.getElementById("prixAchat").value;

    if (prixAchat>0 ) {
        document.getElementById("prixAchatError").innerHTML='';
    }
    else{
        document.getElementById("prixAchatError").innerHTML="Le prix d'achat doit etre positif";
        document.getElementById("prixAchatError").style.color='red';
    }

    var prixVente=document.getElementById("prixVente").value;

    if (prixVente>0 ) {
        document.getElementById("prixVenteError").innerHTML='';
    }
    else{
        document.getElementById("prixVenteError").innerHTML="Le prix de vente doit etre positif";
        document.getElementById("prixVenteError").style.color='red';
    }


    var stock  =document.getElementById("stock").value;

    if (stock>0 ) {
        document.getElementById("stockError").innerHTML='';
    }
    else{
        document.getElementById("stockError").innerHTML="Le stock doit etre positif";
        document.getElementById("stockError").style.color='red';
    }

    var categorie=document.getElementById("selectionPrCategorie").value;
    
    if (categorie!="" ) {
        document.getElementById("categorieSelectionneError").innerHTML='';
    }
    else{
        document.getElementById("categorieSelectionneError").innerHTML="Veuillez choisir la categorie";
        document.getElementById("categorieSelectionneError").style.color='red';
    }

    if ((verifLength(nomProduit,4)) && (reference.length==6)&& (prixAchat>0)&&(prixVente>0 )
    &&(stock>0 )  && (categorie!="" )) {

        var produits=JSON.parse(localStorage.getItem("produits")|| "[]");
        var utilisateurConnecte=JSON.parse(localStorage.getItem("utilisateurConnecte"));
        var idProduit=JSON.parse(localStorage.getItem("idProduit")|| "1");

        var produit={
          id:idProduit,
          nom:nomProduit,
          reference:reference,
          stock:stock,
          prixAchat:prixAchat,
          prixVente:prixVente,
          idCategorie:categorie,
          idEntreprise:utilisateurConnecte.id

        };

        produits.push(produit);
        localStorage.setItem("produits",JSON.stringify(produits));
        localStorage.setItem("idProduit",idProduit+1);
        location.reload();
    }
}

function ajoutCF() {
    var nomCF= document.getElementById("nomCF").value;
    if (verifLength(nomCF,4)) {
        document.getElementById("nomCFError").innerHTML='';
    }
    else{
        document.getElementById("nomCFError").innerHTML='Le nom  doit comporter au moins 4 lettres';
        document.getElementById("nomCFError").style.color='red';
    }
    var immatriculeCF= document.getElementById("immatriculeCF").value;
    if (immatriculeCF!="") {
        document.getElementById("immatriculeCFError").innerHTML='';
    }
    else{
        document.getElementById("immatriculeCFError").innerHTML="Veuillez choisir Immatricule";
        document.getElementById("immatriculeCFError").style.color='red';
    }
    
    var cf = document.getElementsByName("cf");
    var option = "" ;
    for (let i = 0; i < cf.length; i++) {
        if (cf[i].checked) {
            option = cf[i].value ;
            break ;
        }
    }

    // console.log(option);

    if (option.length != 0) {
        document.getElementById("cfError").innerHTML='';
    }
    else{
        document.getElementById("cfError").innerHTML="Veuillez choisir client ou fournisseur" ;
        document.getElementById("cfError").style.color='red';
    }
    if ((verifLength(nomCF,4)) && (immatriculeCF!="") && (option.length != 0)) {
        var cltFrs=JSON.parse(localStorage.getItem("cltFrs")||"[]");
        var idCF=JSON.parse(localStorage.getItem("idCF")||"1");

        var utilisateurConnecte=JSON.parse(localStorage.getItem("utilisateurConnecte"));

        var CltFr={
            id:idCF,
            nom:nomCF,
            immatriculeCF:immatriculeCF,
            cf:option,
            idEntreprise:utilisateurConnecte.id
        };

        cltFrs.push(CltFr);
        localStorage.setItem("cltFrs",JSON.stringify(cltFrs));
        localStorage.setItem("idCF",idCF + 1);
        location.reload();
        
    }
}

function displayProduits() {
    var produits = JSON.parse(localStorage.getItem("produits") || "[]");

    var produitsTable = `` ;
    var utilisateurConnecte = JSON.parse(localStorage.getItem("utilisateurConnecte"));
    var produitsElements = [];

    for (let i = 0; i < produits.length; i++) {
        if (utilisateurConnecte.id == produits[i].idEntreprise) {
            produitsElements.push(produits[i]) ;
        }
    }

    produitsTable = `<table class="table table-dark table-hover">
        <tr>
            <th> Nom</th>
            <th> Reference</th>
            <th> Prix d'achat</th>
            <th> Prix de vente</th>
            <th> Stock</th>
            <th> Categorie</th>
            <th> Actions</th>
        </tr>`;

    for (let i = 0; i < produitsElements.length; i++) {
        var categorieProduit = RechercherObjet(produitsElements[i].idCategorie,"categories");   
        console.log(produitsElements[i].idCategorie);
        console.log(categorieProduit);

    produitsTable = produitsTable + `
    <tr>
    <td> ${produitsElements[i].nom}</td>
    <td> ${produitsElements[i].reference}</td>
    <td> ${produitsElements[i].prixAchat}</td>
    <td> ${produitsElements[i].prixVente}</td>
    <td> ${produitsElements[i].stock}</td>
    <td> ${categorieProduit.nom}</td>

    <td> <button type="button" class="btn btn-warning" onclick="modifierProduit(${produitsElements[i].id})">Modifier</button>
         <button type="button" class="btn btn-danger" onclick="supprimerObjet(${searchPosition(produitsElements[i].id,'produits')},'produits')">Supprimer</button>
    </td> 
    </tr>`;
    }
    produitsTable = produitsTable + `</table>` ;
    document.getElementById("produitsTable").innerHTML= produitsTable ;
}

function modifierProduit(id) {
    var produits = RechercherObjet(id,"produits");
    var modifProduit=`
    
        <div class="mb-3">
            <input type="number" class="form-control" id="newPrixAchat"  value=${produits.prixAchat}> 
            <span id="newPrixAchatProduitError"></span>
        </div>
        <div class="mb-3">
            <input type="number" class="form-control" id="newPrixVente"  value=${produits.prixVente}> 
            <span id="newPrixVenteProduitError"></span>
        </div>

        <div class="mb-3">                   
            <input type="number" class="form-control" id="newStockProduit"  value=${produits.stock}> 
            <span id="newStockProduitError"></span>
        </div>
    
        <button type="button" class="btn btn-primary" style="margin-left: 40%;" onclick="validerModifProduit(${produits.id})">Modifier</button>
    `;
    document.getElementById("modifProduit").innerHTML=modifProduit;   
}

function validerModifProduit(id) {
    var newPrixAchat = document.getElementById("newPrixAchat").value;
    if (newPrixAchat > 0) {
        document.getElementById("newPrixAchatProduitError").innerHTML='';
    }
    else{
        document.getElementById("newPrixAchatProduitError").innerHTML="Le nouveau prix d'achat doit être strictement positif";
        document.getElementById("newPrixAchatProduitError").style.color='red';
    }

    var newPrixVente = document.getElementById("newPrixVente").value;
    if (newPrixVente > 0) {
        document.getElementById("newPrixVenteProduitError").innerHTML='';
    }
    else{
        document.getElementById("newPrixVenteProduitError").innerHTML="Le nouveau prix de vente doit être strictement positif";
        document.getElementById("newPrixVenteProduitError").style.color='red';
    }
    
    var newStockProduit = document.getElementById("newStockProduit").value;
    if (newStockProduit > 0) {
        document.getElementById("newStockProduitError").innerHTML='';
    }
    else{
        document.getElementById("newStockProduitError").innerHTML="Le nouveau stock doit être strictement positif";
        document.getElementById("newStockProduitError").style.color='red';
    }


if ((newPrixAchat > 0) && (newPrixVente > 0) && (newStockProduit > 0)) {
    var produits = JSON.parse(localStorage.getItem("produits") || "[]");
    for (let i = 0; i < produits.length; i++) {
        if (produits[i].id == id) {
            produits[i].prixAchat = newPrixAchat;
            produits[i].prixVente = newPrixVente ;
            produits[i].stock = newStockProduit ;
        }
    }
    localStorage.setItem("produits",JSON.stringify(produits));
    location.reload();
}
}

// function modifierCF(id) {
//     var cltFRC =RechercherObjet(id,"categories");
//     console.log(categorie.descriptionCategorie);
//     var ModifCF=`
//     <div class="mb-3">
                            
//     <input type="text" class="form-control" id="newprixAchat"  value=${cltFRC.nom}> 
//         <span id="newprixAchatError"></span>
// </div>
// <div class="mb-3">
                            
//     <input type="text" class="form-control" id="newprixVente"  value=${cltFRC.nom}> 
//         <span id="newprixVenteError"></span>
// </div>
// <div class="mb-3">
                            
//     <input type="text" class="form-control" id="newStock"  value=${cltFRC.nom}> 
//         <span id="newStockError"></span>
// </div> 
// <div class="mb-3">
//     <input class="form-control" id="newDescriptionCategorie" rows="3"  >${cltFRC.descriptionCategorie}
//     <span id="newDescriptionCategorieError"></span>

// </div>
// <button type="button" class="btn btn-warning" style="margin-left: 40%;" onclick="validerModifCategorie(${categorie.id})">Modifier</button>
//     `;
//     document.getElementById("ModifCategorie").innerHTML=ModifCategorie;


    
// }
function chercherFournisseur() {
    var cltFrs=JSON.parse(localStorage.getItem("cltFrs")||"[]");
    var utilisateurConnecte= JSON.parse(localStorage.getItem("utilisateurConnecte"));
    var FRS=[];
    for (let i = 0; i < cltFrs.length; i++) {
        if ((cltFrs[i].cf=="fournisseur") && (utilisateurConnecte.id==cltFrs[i].idEntreprise)) {
            FRS.push(cltFrs[i]);
        }
    }

    var selectFrs=`
<select class="form-select" aria-label="Default select example" id="mySelect">
  <option selected value="">Selectionner Fournisseur</option>`;
  for (let i = 0; i < FRS.length; i++) {
  var selectFrs= selectFrs + `
  <option value=${FRS[i].id}>${FRS[i].nom}</option>`;

  }
  selectFrs=selectFrs+ `</select>
  <span id="idFournisseurError"></span>
  `;
  
  selectFrs=selectFrs+ `<button type="button" class="btn btn-primary" style="margin-left: 40%; margin-top: 20px;" onclick="selectionnerFRS()">Selectionner</button>
  `;
  document.getElementById("selectFrs").innerHTML=selectFrs;
}
/* function handleSelectChange(event) {
    var selectElement = event.target;
    var value = selectElement.value;
    return(value);
}
  function afficherProduitFRS(value) {
      console.log(value);
      
  } */      
 function selectionnerFRS() {
    var idFournisseur=document.getElementById("mySelect").value;
    if(idFournisseur!=""){
        var btn= `<button type="button" class="btn btn-primary" style="margin-left: 40%; margin-top: 20px;" onclick="afficherPrFRS(${idFournisseur})">Chercher</button>`;
        document.getElementById("btn").innerHTML=btn;
        document.getElementById("idFournisseurError").innerHTML="";
    }else{
        document.getElementById("idFournisseurError").innerHTML=" Veuiller choisir Fournisseur";
        document.getElementById("idFournisseurError").style.color=" red";
    }   
     
 }   
    
function afficherPrFRS(id) {
    
    var fournisseur = RechercherObjet(id,"cltFrs");
    var utilisateurs = JSON.parse(localStorage.getItem("utilisateurs") || "[]");
    var idFournisseur;
    for (let i = 0; i < utilisateurs.length; i++) {
        if (fournisseur.immatriculeCF == utilisateurs[i].immatriculeFiscale) {
            idFournisseur= utilisateurs[i].id;
        }
        
    }
    var produits = JSON.parse(localStorage.getItem("produits") || "[]");

    produitsTable = `<table class="table table-dark table-hover">
    <tr>
        <th> Nom</th>
        <th> Reference</th>
        <th> Prix</th>
        <th> Actions</th>
    </tr>`;

    for (let i = 0; i < produits.length; i++) {
        if(idFournisseur == produits[i].idEntreprise) {

            produitsTable = produitsTable + `
            <tr>
            <td> ${produits[i].nom}</td>
            <td> ${produits[i].reference}</td>
            <td> ${produits[i].prixVente}</td>
          
            <td> <button type="button" class="btn btn-warning" onclick="">Commander</button>
            </td> 
            </tr>`;

        }
    }
produitsTable = produitsTable + `</table>` ;
document.getElementById("produitsFrsTable").innerHTML= produitsTable ;

}

    

