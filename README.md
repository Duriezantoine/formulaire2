# formulaire2

<?php

$errors = [];
if ($_SERVER['REQUEST_METHOD'] ==="POST"){
  var_dump($_POST['sujet']) ;
  if(empty($_POST['email'])){
    $errors['email']='email est demandé ';
  
  }
  if(!filter_var($_POST['email'],FILTER_VALIDATE_EMAIL)) {
  $errors['email_nonvalide'] ='email non valide ';

  }
  if(empty($_POST['nom'])){
 
    $errors['nom'] = 'Le prenom est demandé';
  }
  if(empty($_POST['prenom'])){
    $errors['prenom'] = 'Le prenom est demandé ';
  }
  if(empty($_POST['telephone'])){
    $errors['telephone'] = 'Le téléphone est demandé ';
  }
  if($_POST['sujet'] === 'default'){
    $errors['sujet'] = 'Le sujet  est demandé ';
  }
  if(empty($_POST['message'])){
    $errors['message'] = 'Le message  est demandé ';
  }
  if (empty($errors)){
    header('Location: form.php') ; 
  }
}
?>
<!doctype html>
<html lang="fr">
<head>

  <meta charset="utf-8">
  <title>Titre de la page</title>
  <link rel="stylesheet" href="style.css">
  <script src="script.js"></script>
</head>
<body>







<div class="contener">

<form   method="post">

    <div>

      <label  for="nom">Nom :</label>

      <input  type="text"  id="nom"  name="nom">


                <?php

if (isset($errors ['nom'])){
  echo $errors ['nom'] ;

} ?>

    </div>

    <div> 
</br>
    <label for="prenom">Prenom :</label>

    <input type="text" id="prenom" name="prenom">


    <?php

if (isset($errors ['prenom'])){
  echo $errors ['prenom'] ;

} ?>

    </div>

</br>


    <div>

            <label for="telephone"> Telephone : </label>

            <input type="telephone" id="telephone" name="telephone">


                <?php

if (isset($errors ['telephone'])){
  echo $errors ['telephone'] ;

} ?>

   
    </div>
</br>
    <div>

      <label  for="email">Courriel :</label>

        <input  type="email"  id="email"  name="email">

                <?php

                  if (isset($errors ['email'])){
                    echo $errors ['email'] ;

                  }
                  if (isset($errors['email_nonvalide'])){
                  echo $errors['email_nonvalide'];
                  }

                ?>
    </div>

    <div>

        <label for="sujet"> Sujet :</label>

        <select id ="sujet" name="sujet">

        <option value="default"> select </option>


        <option value="1tmts"> 1tmts </option>

        <option value="2tmts"> 2tmts </option>

        <option value="3tmts"> 3tmts </option>

        <?php

if (isset($errors ['sujet'])){
  echo $errors ['sujet'] ;

} ?>

        </select>


    <div>

      <label  for="message">Message :</label>

      <textarea  id="message"  name="message"></textarea>


                <?php

if (isset($errors ['message'])){
  echo $errors ['message'] ;

} ?>
    </div>

    <div  class="button">

      <button  type="submit">Envoyer votre message</button>

    </div>

  </form>
  </div>
</body> 
</body> 
