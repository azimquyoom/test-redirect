<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Continue</title>
</head>
<body>

<form id="continue_action" method="GET" action="https://gateway.example.zscaler.net:443/_sm_ctn">
    <input type="hidden" name="_sm_url" id="_sm_url">
    <input type="hidden" name="_sm_rid" id="_sm_rid">
    <input type="hidden" name="_sm_cat" id="_sm_cat">
    <input type="submit" value="Continue" id="submitButton">
</form>

<script>
// Function to get URL parameters
function getParameterByName(name) {
    name = name.replace(/[[]/, "\\[").replace(/[\]]/, "\\]");
    const regex = new RegExp("[\\?&]" + name + "=([^&#]*)");
    const results = regex.exec(location.search);
    return results === null ? "" : decodeURIComponent(results[1].replace(/\+/g, " "));
}

// Populate hidden fields
document.getElementById('_sm_url').value = getParameterByName('url');

let zsq = getParameterByName('zsq');
document.getElementById('_sm_rid').value = zsq.split('zsq')[0]; // split like your PHP

document.getElementById('_sm_cat').value = getParameterByName('cat');
</script>

</body>
</html>
