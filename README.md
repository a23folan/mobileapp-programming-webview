
# Rapport

### steg 1

först döper om appnamet under strings.xml:

```
<string name="app_name">2-7 i shack</string>
```
* bytte TextView till "Webview" i activity_main.xml
* Under Webview lades till 

> <uses-permission android:name="android.permission.INTERNET" />


för internet under AndroidManifest.xml och 
> android:id="@+id/my_webview"

under activity.xml för ID

### steg 2

```java 
//skapar class för WebView
    private WebView myWebView;
    //laddar in den externa sidan
    public void showExternalWebPage(){
        myWebView.loadUrl("https://www.chess.com/member/arthmauler");
    }
    //laddar in den interna sidan
    public void showInternalWebPage(){
        myWebView.loadUrl("file:///android_asset/about.html");
    }
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Toolbar toolbar = findViewById(R.id.toolbar);
        setSupportActionBar(toolbar);
        
        //Justerar WebView enligt beskrivning
        //vilket inkluderar ID, client och tillåtelse av Javascript        
     
        myWebView = findViewById(R.id.my_webview);
        myWebView.setWebViewClient(new WebViewClient());
        myWebView.getSettings().setJavaScriptEnabled(true);
```

### steg 3 - ladda in external och internal web view med knapp 

I Slutet hämtas functionerna för external och internal WebPage in under 

```java
    if (id == R.id.action_external_web) {
            Log.d("==>","Will display external web page");
            //external view hämtas in
            showExternalWebPage();
            return true;
        }

    if (id == R.id.action_internal_web) {
            Log.d("==>","Will display internal web page");
            //internal view hämtas in
            showInternalWebPage();
            return true;
        }
```
detta ligger under onOptionsItemSelected() vilket är ansvarig för menyn

Screenshots tas av både internal och external view, dessa läggs under mobileapp-programming-webviewså vi kan nå bilderna lokalt

![externalView](external_web.png)
![internalView](internal_web.png)

