
<?php 
require '_functions.php';
include 'partials/top.php';

consoleLog($_POST, 'POST');
consoleLog($_FILES, 'FILES');

if(empty($_POST) && empty($_FILES)) die ('There was a problem uploading the file (probably too large)');

// Get image data and type of uploaded file from the $_FILES super-global
[
    'data' => $imageData,
    'type' => $imageType
] = uploadedImageData($_FILES['image']);


// Get standard form data
$name = $_POST['name'];
$description = $_POST['description'];
$theme = $_POST['theme'];

$db = connectToDB();

//Setup a query to insert all company info
$query = 'INSERT INTO examples
           (`name`, `description`, theme, image_data, image_type) 
           VALUES (?, ?, ?, ?, ?)';

//Attempt to run the query
try {
    $stmt = $db->prepare($query);
    $stmt->execute([$name, $description, $theme, $imageData, $imageType]);
}

catch (PDOException $e) {
    consoleLog($e->getMessage(), 'DB Upload Picture', ERROR);
    die('There was an error adding picture to the database. Please try again.');
}

header('location: form-example.php')
?>

