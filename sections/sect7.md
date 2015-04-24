# Facebook OA / AI2 – Week 7 (March 11 – March 18)

This week, I was just up recovering from Dengue. Missed a midterm, but making up for it after the period. Lots of schoolwork catching up this week.

I have managed to connect the interface between Java and SimplePhaser, and it looks really neat now. It is a relief as the theory behind our program implementation works!

Wrote an app to test things out. And so this is how bi-directional callbacks actually work!

## Java to JS

    WebView.loadUrl("javascript:myJavascriptFunction()");
    

## JS to Java

This is what you do on the Java side, exposing the interface:

    /** Java **/
    @JavascriptInterface
    public void showToast(String toast) {
        Toast.makeText(mContext, toast, Toast.LENGTH_SHORT).show();
    }
    ...
    // from http://developer.android.com/guide/webapps/webview.html
    WebView webView = (WebView) findViewById(R.id.webview);
    webView.addJavascriptInterface(new WebAppInterface(this), "Android");
    

And on the JS side, call it like this:

    function showAndroidToast(toast) {
        Android.showToast(toast);
    }
    

For next steps, I will work on the collision handling.