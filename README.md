
# Rapport

**Skriv din rapport här!**

_Du kan ta bort all text som finns sedan tidigare_.

## Följande grundsyn gäller dugga-svar:

I denna uppgift har det användts WebView för att kunna visa en extern hemsidan samt en intern hemsidan i min app.
Det första som behövdes göras var att lägga till en WebView i activity_main filen i Layouten.

```
<WebView
    android:id="@+id/webview"
    android:layout_height="match_parent"
    android:layout_width="match_parent"
    />
```
Nu när WebViewn finns i appen behöves det läggas till vad som ska visas. Det finns två olika sidor som visas en extern och en intern. Det externa sidan är his.se och den interna är en super simpel HTML fil som jag har gjort. 
För att kunna byta mellan sidorna behövs det läggas till actions i en meny funktion. Detta gjordes på detta sätt.

```
if (id == R.id.action_external_web) {
    Log.d("==>","Will display external web page");
    showExternalWebPage();
    return true;
}

if (id == R.id.action_internal_web) {
    Log.d("==>","Will display internal web page");
    showInternalWebPage();
    return true;
}
```
Det var även ett par saker som behövdes läggas till för att WebViewn skulle fungera som behövde läggas till i MainActivity Java filen, detta var exempelvis så att javascript får ändra appen. 

```
myWebView = findViewById(R.id.webview);
myWebView.setWebViewClient(new WebViewClient()); // Do not open in Chrome
myWebView.loadUrl("https://his.se");
myWebView.loadUrl("file:///android_asset/about.html");
WebView myWebView = (WebView) findViewById(R.id.webview);
WebSettings webSettings = myWebView.getSettings();
webSettings.setJavaScriptEnabled(true);
```

![](internal.png)
![](external.png)
