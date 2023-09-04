<html><head>  
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <style type="text/css">
            /* CSS */
            * {
                font-family: Verdana, Geneva, Tahoma, sans-serif;
            }
            
            .button-37 {
                margin: 20px;
                background-color: #13aa52;
                border: 1px solid #13aa52;
                border-radius: 4px;
                box-shadow: rgba(0, 0, 0, .1) 0 2px 4px 0;
                box-sizing: border-box;
                color: #fff;
                cursor: pointer;
                font-family: "Akzidenz Grotesk BQ Medium", -apple-system, BlinkMacSystemFont, sans-serif;
                font-size: 16px;
                font-weight: 400;
                outline: none;
                outline: 0;
                padding: 10px 25px;
                text-align: center;
                transform: translateY(0);
                transition: transform 150ms, box-shadow 150ms;
                user-select: none;
                -webkit-user-select: none;
                touch-action: manipulation;
            }
            
            p {
                text-align: center;
                font-size: large;
            }
            
            .button-37:hover {
                box-shadow: rgba(0, 0, 0, .15) 0 3px 9px 0;
                transform: translateY(-2px);
            }
            
            @media (min-width: 768px) {
                .button-37 {
                    padding: 10px 30px;
                }
            }
            </style>
        <title>Self-Reg testing page</title>
        <script>
            function gettRegistrationFinishedMessageHandler() { 
                if (isAndroid()) {
                    window.WebViewJSBridge.onRegistrationFinished();
                } else {
                    window.webkit.messageHandlers.gettRegistrationFinishedMessageHandler.postMessage(
                        {
                            "status": "success"
                        }
                        );
                    }
                }

                function onCCCSuccessfullyAdded() {
                    if (isAndroid()) {
                        window.WebViewJSBridge.onCCCSuccessfullyCreated();
                    } else {
                        window.webkit.messageHandlers.onCCCSuccessfullyCreated.postMessage('card successfully Added! close the webview');
                    }
                }
                
                function onCompanyCreatedSuccessfully() {
                    if (isAndroid()) {
                        window.WebViewJSBridge.onCompanyCreatedSuccessfully();
                    } else {
                        window.webkit.messageHandlers.onCompanyCreatedSuccessfully.postMessage('Company created! call "create session"');
                    }
                }
                
                function onCompanyCreatedFailure() {
                    if (isAndroid()) {
                        window.WebViewJSBridge.onCompanyCreatedFailure();
                    } else {
                        window.webkit.messageHandlers.onCompanyCreatedFailure.postMessage('Company created! call "create session"');
                    }
                }
                
                function onSkipAddCreditCard() { 
                    if (isAndroid()) {
                        window.WebViewJSBridge.onSkipAddCreditCard();
                    } else {
                        window.webkit.messageHandlers.onSkipAddCreditCard.postMessage('Add CCC skipped - close self-reg');
                    }
                }
                
                function redirectInnerHttps() {
                    window.location.assign('https://business.gett.com');
                }

                function redirectInnerHttp() {
                    window.location.assign('http://business.gett.com');
                }

                function redirectOuterHttps() {
                    window.location.assign('https://picsum.photos');
                }    
                
                function redirectOuterHttp() {
                    window.location.assign('http://picsum.photos');
                }
                
                function linkOuter() {
                    window.location.href='https://picsum.photos';
                }
                
                function linkInner() {
                    window.location.href='https://il.gett.com';
                }
                                
                function readOTT() {
                    let ottElement = document.getElementById("ott_value");
                    if (window.location.hash) {
                        ottElement.innerHTML = window.location.hash;
                    } else {
                        ottElement.innerHTML = "No OTT 😞";
                    }
                }
                
                function isAndroid() {
                    return window.navigator.userAgent.toLowerCase().includes("android");
                }
                
                function onLoad() {
                    readOTT();
                    readOS();
                    readUserAgent();
                }
                
                function readOS() {
                    let osElement = document.getElementById("os_type");
                    if (isAndroid()) {
                        osElement.innerHTML = "Android";
                    } else {
                        osElement.innerHTML = "iOS";
                    }
                }
                
                function readUserAgent() {
                    document.getElementById("user_agent").innerHTML = navigator.userAgent;
                }

                window.onload = onLoad;
            </script>
    </head>
    
    <body>
        <h1 style="text-align: center;">Self Reg - events testing page</h1>
        <p>
            OTT: <span id="ott_value">No OTT 😞</span>
        </p>
        <div>
            <button class="button-37" onclick="gettRegistrationFinishedMessageHandler()">Legacy completion</button><br>
            <button class="button-37" onclick="onCCCSuccessfullyAdded()">CCC successfully Added</button><br>
            <button class="button-37" onclick="onCompanyCreatedSuccessfully()">Company created</button><br>
            <button class="button-37" onclick="onCompanyCreatedFailure()">Company creation failed</button><br>
            <button class="button-37" onclick="onSkipAddCreditCard()">Skip Credit Card</button><br>
        </div>
        <div>
            <p style="text-align: start;">Redirect:</p>
            <button class="button-37" onclick="redirectInnerHttps()" style="background-color:#16513e">Inner HTTPS</button><br>
            <button class="button-37" onclick="redirectInnerHttp()" style="background-color:#16513e">Inner HTTP</button><br>
            <button class="button-37" onclick="redirectOuterHttps()" style="background-color:#16513e">Outer HTTPS</button><br>
            <button class="button-37" onclick="redirectOuterHttp()" style="background-color:#16513e">Outer HTTP</button><br>
        </div>
        <div>
            <p style="text-align: start;">Link:</p>
            <a href="https://business.gett.com/" class="button">Inner</a>
            <br>
            <br>
            <a href="https://picsum.photos/" class="button">Outer</a><br>
        </div>
        <p>
            OS detected: <span id="os_type">iOS</span>
            <br>
            User Agent: <span id="user_agent">Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/116.0.0.0 Safari/537.36</span>
        </p>
        <p style="font-size: 90%;">version 10000008</p>
    
</body></html>
