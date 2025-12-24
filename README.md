<?php
$url         = filter_input(INPUT_GET, 'url', FILTER_SANITIZE_URL);
$referer     = filter_input(INPUT_GET, 'referer', FILTER_SANITIZE_URL);
$reason      = filter_input(INPUT_GET, 'reason', FILTER_SANITIZE_SPECIAL_CHARS);
$reason_code = filter_input(INPUT_GET, 'reasoncode', FILTER_SANITIZE_NUMBER_INT);
$timebound   = filter_input(INPUT_GET, 'timebound', FILTER_SANITIZE_SPECIAL_CHARS);
$action      = filter_input(INPUT_GET, 'action', FILTER_SANITIZE_SPECIAL_CHARS);
$kind        = filter_input(INPUT_GET, 'kind', FILTER_SANITIZE_SPECIAL_CHARS);
$rule        = filter_input(INPUT_GET, 'rule', FILTER_SANITIZE_SPECIAL_CHARS);
$cat         = filter_input(INPUT_GET, 'cat', FILTER_SANITIZE_SPECIAL_CHARS);
$user        = filter_input(INPUT_GET, 'user', FILTER_SANITIZE_SPECIAL_CHARS);
$lang        = filter_input(INPUT_GET, 'lang', FILTER_SANITIZE_SPECIAL_CHARS);
$zsq_param   = filter_input(INPUT_GET, 'zsq', FILTER_DEFAULT);

$zsq = $zsq_param !== null ? explode("zsq", $zsq_param) : [];
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
