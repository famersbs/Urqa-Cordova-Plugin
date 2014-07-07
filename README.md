Urqa-Cordova-Plugin v0.1
===================

Urqa-Cordova-Plugin

# Menual Install

## js file copy

cp -f ../Urqa-Cordova-Plugin/www/js/stacktrace.js ./www/js/stacktrace.js
cp -f ../Urqa-Cordova-Plugin/www/js/urqaplugin.js ./www/js/urqaplugin.js


## src file copy
cp -rf ../Urqa-Cordova-Plugin/src/* ./platforms/android/src/
cp -rf ../Urqa-Cordova-Plugin/libs/* ./platforms/android/libs/


# Sample index.html

```html
<script type="text/javascript" src="cordova.js"></script>
<script type="text/javascript" src="js/index.js"></script>
<script type="text/javascript" src="js/stacktrace.js"></script>
<script type="text/javascript" src="js/urqaplugin.js"></script>
<script type="text/javascript">

    //var cordova = require('cordova');
    //cordova.exec = cordova.exec || require('cordova/exec');
    
    var writelog = function( log_msg ){
        document.getElementById("test_log").value = log_msg;
    };

    writelog( "zero" );

    app.initialize();

    writelog( "first " + cordova );

    var urqa = createUrqa();
    
    writelog( "second " + urqa.send_error );
    function ttt(){
        try{
            var te = null;
            te.toString();
        }catch(err){
            urqa.send_error( err );    
        }
    };

    ttt();

    function ttt2(){
        urqa.send_msg( "This is Test Msg" );
    }

    ttt2();

    writelog( "end ");

</script>
```

# Links

Stacktrace.js : http://stacktracejs.com/