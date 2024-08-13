
<?php 
require '_functions.php';
include 'partials/top.php';

consoleLog($_POST, 'POST Data');

// Get form data
$theme = $_POST['theme'];
$description = $_POST['description'];


$db = connectToDB();

//Setup a query to insert all company info
$query = 'INSERT INTO themes
           (theme, `description`) 
           VALUES (?, ?)';

//Attempt to run the query
try {
    $stmt = $db->prepare($query);
    $stmt->execute([$theme, $description]);
}

catch (PDOException $e) {
    consoleLog($e->getMessage(),'DB List Fetch', ERROR);
    die('There was an error sending data to the database');
}

header('location: form-theme.php')
?>

