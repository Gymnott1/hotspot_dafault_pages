## REDIRECT TO LINK

```
<-- file login.html -->
<body>
    <script>
        const mac = "$(mac)";
        const linkLoginOnly = "$(link-login-only)";
        const linkOrig = "$(link-orig)";
        const chapId = "$(chap-id)";
        const chapChallenge = "$(chap-challenge)";

        function detectAndRedirect() {
            if (mac && mac !== '' && mac !== '$' + '(mac)') {

                document.getElementById('statusText').innerText = "Device detected. Redirecting...";

                const baseUrl = "http://example.com/hotspot";
                const params = new URLSearchParams({
                    mac: mac,
                    'link-login-only': linkLoginOnly,
                    'chap-id': chapId,
                    'chap-challenge': chapChallenge,
                    'link-orig': linkOrig
                });

                window.location.href = baseUrl + "?" + params.toString();
            } else {
                showError();
            }
        }

        function showError() {
            document.getElementById('wifiLoader').style.display = 'none';
            document.getElementById('errorContent').style.display = 'block';
            document.getElementById('statusText').innerText = "Connection Error";
        }

        detectAndRedirect();
    </script>
</body>
```
