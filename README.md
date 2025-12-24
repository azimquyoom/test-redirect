<?php
$url = $_GET['url'];
$referer = $_GET['referer'];
$reason = $_GET['reason'];
$reason_code = $_GET['reasoncode'];
$timebound = $_GET['timebound'];
$action = $_GET['action'];
$kind = $_GET['kind'];
$rule = $_GET['rule'];
$cat = $_GET['cat'];
$user = $_GET['user'];
$lang = $_GET['lang'];
$zsq = explode("zsq", $_GET['zsq'];
?>

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Caution Notification</title>
<style>
  body { font-family: Arial, sans-serif; background-color: #fffbe6; color: #333; }
  .container { max-width: 600px; margin: 50px auto; padding: 20px; border: 2px solid #f1c40f; background-color: #fff; border-radius: 5px; }
  h1 { color: #d35400; }
  p { font-size: 16px; }
  #submitButton { background-color: #f39c12; color: white; border: none; padding: 10px 20px; font-size: 16px; cursor: pointer; border-radius: 3px; }
  #submitButton:hover { background-color: #e67e22; }
</style>
</head>
<body>
<div class="container">
  <h1>Caution</h1>
  <p>You are about to visit a site that may violate your organization's internet usage policy.</p>
  <p><strong>Reason:</strong> <?php echo htmlspecialchars($reason); ?></p>
  <p>If you understand the risk, you may continue by clicking below.</p>

  <form id="continue_action" method="GET" action="https://gateway.zscalerone.net:443/_sm_ctn">
    <input type="hidden" name="_sm_url" value="<?php $_GET['url'];?>">
    <input type="hidden" name="_sm_rid" value="<?php split('zsq', $_GET[zsq]);?>">
    <input type="hidden" name="_sm_cat" value="<?php $_GET['cat'];?>">
    <input type="submit" value="Continue" id="submitButton">
  </form>
</div>
</body>
</html>
