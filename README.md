<!DOCTYPE html>
<!-- saved from url=(0120)http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb -->
<html lang="fr-fr"><head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    

    <title>Recommander_Systems_Project</title>
    
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <link rel="stylesheet" href="./README_files/jquery-ui.min.css" type="text/css">
    <link rel="stylesheet" href="./README_files/jquery.typeahead.min.css" type="text/css">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    


<script type="text/javascript" src="./README_files/MathJax.js.download" charset="utf-8"></script>

<script type="text/javascript">
// MathJax disabled, set as null to distingish from *missing* MathJax,
// where it will be undefined, and should prompt a dialog later.
window.mathjax_url = "/static/components/MathJax/MathJax.js";
</script>

<link rel="stylesheet" href="./README_files/bootstrap-tour.min.css" type="text/css">
<link rel="stylesheet" href="./README_files/codemirror.css">


    <link rel="stylesheet" href="./README_files/style.min.css" type="text/css">
    

<link rel="stylesheet" href="./README_files/override.css" type="text/css">
<link rel="stylesheet" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb" id="kernel-css" type="text/css">


    <link rel="stylesheet" href="./README_files/custom.css" type="text/css">
    <script src="./README_files/promise.min.js.download" type="text/javascript" charset="utf-8"></script>
    <script src="./README_files/index.js.download" type="text/javascript"></script>
    <script src="./README_files/index.js(1).download" type="text/javascript"></script>
    <script src="./README_files/index.js(2).download" type="text/javascript"></script>
    <script src="./README_files/require.js.download" type="text/javascript" charset="utf-8"></script>
    <script>
      require.config({
          
          urlArgs: "v=20190305083854",
          
          baseUrl: '/static/',
          paths: {
            'auth/js/main': 'auth/js/main.min',
            custom : '/custom',
            nbextensions : '/nbextensions',
            kernelspecs : '/kernelspecs',
            underscore : 'components/underscore/underscore-min',
            backbone : 'components/backbone/backbone-min',
            jed: 'components/jed/jed',
            jquery: 'components/jquery/jquery.min',
            json: 'components/requirejs-plugins/src/json',
            text: 'components/requirejs-text/text',
            bootstrap: 'components/bootstrap/js/bootstrap.min',
            bootstraptour: 'components/bootstrap-tour/build/js/bootstrap-tour.min',
            'jquery-ui': 'components/jquery-ui/ui/minified/jquery-ui.min',
            moment: 'components/moment/min/moment-with-locales',
            codemirror: 'components/codemirror',
            termjs: 'components/xterm.js/xterm',
            typeahead: 'components/jquery-typeahead/dist/jquery.typeahead.min',
          },
          map: { // for backward compatibility
              "*": {
                  "jqueryui": "jquery-ui",
              }
          },
          shim: {
            typeahead: {
              deps: ["jquery"],
              exports: "typeahead"
            },
            underscore: {
              exports: '_'
            },
            backbone: {
              deps: ["underscore", "jquery"],
              exports: "Backbone"
            },
            bootstrap: {
              deps: ["jquery"],
              exports: "bootstrap"
            },
            bootstraptour: {
              deps: ["bootstrap"],
              exports: "Tour"
            },
            "jquery-ui": {
              deps: ["jquery"],
              exports: "$"
            }
          },
          waitSeconds: 30,
      });

      require.config({
          map: {
              '*':{
                'contents': 'services/contents',
              }
          }
      });

      // error-catching custom.js shim.
      define("custom", function (require, exports, module) {
          try {
              var custom = require('custom/custom');
              console.debug('loaded custom.js');
              return custom;
          } catch (e) {
              console.error("error loading custom.js", e);
              return {};
          }
      })

    document.nbjs_translations = {"domain": "nbjs", "locale_data": {"nbjs": {"": {"domain": "nbjs"}}}};
    document.documentElement.lang = navigator.language.toLowerCase();
    </script>

    
    

<script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="services/contents" src="./README_files/contents.js.download"></script><style type="text/css">.MathJax_Hover_Frame {border-radius: .25em; -webkit-border-radius: .25em; -moz-border-radius: .25em; -khtml-border-radius: .25em; box-shadow: 0px 0px 15px #83A; -webkit-box-shadow: 0px 0px 15px #83A; -moz-box-shadow: 0px 0px 15px #83A; -khtml-box-shadow: 0px 0px 15px #83A; border: 1px solid #A6D ! important; display: inline-block; position: absolute}
.MathJax_Menu_Button .MathJax_Hover_Arrow {position: absolute; cursor: pointer; display: inline-block; border: 2px solid #AAA; border-radius: 4px; -webkit-border-radius: 4px; -moz-border-radius: 4px; -khtml-border-radius: 4px; font-family: 'Courier New',Courier; font-size: 9px; color: #F0F0F0}
.MathJax_Menu_Button .MathJax_Hover_Arrow span {display: block; background-color: #AAA; border: 1px solid; border-radius: 3px; line-height: 0; padding: 4px}
.MathJax_Hover_Arrow:hover {color: white!important; border: 2px solid #CCC!important}
.MathJax_Hover_Arrow:hover span {background-color: #CCC!important}
</style><style type="text/css">#MathJax_About {position: fixed; left: 50%; width: auto; text-align: center; border: 3px outset; padding: 1em 2em; background-color: #DDDDDD; color: black; cursor: default; font-family: message-box; font-size: 120%; font-style: normal; text-indent: 0; text-transform: none; line-height: normal; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; z-index: 201; border-radius: 15px; -webkit-border-radius: 15px; -moz-border-radius: 15px; -khtml-border-radius: 15px; box-shadow: 0px 10px 20px #808080; -webkit-box-shadow: 0px 10px 20px #808080; -moz-box-shadow: 0px 10px 20px #808080; -khtml-box-shadow: 0px 10px 20px #808080; filter: progid:DXImageTransform.Microsoft.dropshadow(OffX=2, OffY=2, Color='gray', Positive='true')}
#MathJax_About.MathJax_MousePost {outline: none}
.MathJax_Menu {position: absolute; background-color: white; color: black; width: auto; padding: 2px; border: 1px solid #CCCCCC; margin: 0; cursor: default; font: menu; text-align: left; text-indent: 0; text-transform: none; line-height: normal; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; z-index: 201; box-shadow: 0px 10px 20px #808080; -webkit-box-shadow: 0px 10px 20px #808080; -moz-box-shadow: 0px 10px 20px #808080; -khtml-box-shadow: 0px 10px 20px #808080; filter: progid:DXImageTransform.Microsoft.dropshadow(OffX=2, OffY=2, Color='gray', Positive='true')}
.MathJax_MenuItem {padding: 2px 2em; background: transparent}
.MathJax_MenuArrow {position: absolute; right: .5em; padding-top: .25em; color: #666666; font-size: .75em}
.MathJax_MenuActive .MathJax_MenuArrow {color: white}
.MathJax_MenuArrow.RTL {left: .5em; right: auto}
.MathJax_MenuCheck {position: absolute; left: .7em}
.MathJax_MenuCheck.RTL {right: .7em; left: auto}
.MathJax_MenuRadioCheck {position: absolute; left: 1em}
.MathJax_MenuRadioCheck.RTL {right: 1em; left: auto}
.MathJax_MenuLabel {padding: 2px 2em 4px 1.33em; font-style: italic}
.MathJax_MenuRule {border-top: 1px solid #CCCCCC; margin: 4px 1px 0px}
.MathJax_MenuDisabled {color: GrayText}
.MathJax_MenuActive {background-color: Highlight; color: HighlightText}
.MathJax_MenuDisabled:focus, .MathJax_MenuLabel:focus {background-color: #E8E8E8}
.MathJax_ContextMenu:focus {outline: none}
.MathJax_ContextMenu .MathJax_MenuItem:focus {outline: none}
#MathJax_AboutClose {top: .2em; right: .2em}
.MathJax_Menu .MathJax_MenuClose {top: -10px; left: -10px}
.MathJax_MenuClose {position: absolute; cursor: pointer; display: inline-block; border: 2px solid #AAA; border-radius: 18px; -webkit-border-radius: 18px; -moz-border-radius: 18px; -khtml-border-radius: 18px; font-family: 'Courier New',Courier; font-size: 24px; color: #F0F0F0}
.MathJax_MenuClose span {display: block; background-color: #AAA; border: 1.5px solid; border-radius: 18px; -webkit-border-radius: 18px; -moz-border-radius: 18px; -khtml-border-radius: 18px; line-height: 0; padding: 8px 0 6px}
.MathJax_MenuClose:hover {color: white!important; border: 2px solid #CCC!important}
.MathJax_MenuClose:hover span {background-color: #CCC!important}
.MathJax_MenuClose:hover:focus {outline: none}
</style><style type="text/css">.MathJax_Preview .MJXf-math {color: inherit!important}
</style><style type="text/css">.MJX_Assistive_MathML {position: absolute!important; top: 0; left: 0; clip: rect(1px, 1px, 1px, 1px); padding: 1px 0 0 0!important; border: 0!important; height: 1px!important; width: 1px!important; overflow: hidden!important; display: block!important; -webkit-touch-callout: none; -webkit-user-select: none; -khtml-user-select: none; -moz-user-select: none; -ms-user-select: none; user-select: none}
.MJX_Assistive_MathML.MJX_Assistive_MathML_Block {width: 100%!important}
</style><style type="text/css">#MathJax_Zoom {position: absolute; background-color: #F0F0F0; overflow: auto; display: block; z-index: 301; padding: .5em; border: 1px solid black; margin: 0; font-weight: normal; font-style: normal; text-align: left; text-indent: 0; text-transform: none; line-height: normal; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; -webkit-box-sizing: content-box; -moz-box-sizing: content-box; box-sizing: content-box; box-shadow: 5px 5px 15px #AAAAAA; -webkit-box-shadow: 5px 5px 15px #AAAAAA; -moz-box-shadow: 5px 5px 15px #AAAAAA; -khtml-box-shadow: 5px 5px 15px #AAAAAA; filter: progid:DXImageTransform.Microsoft.dropshadow(OffX=2, OffY=2, Color='gray', Positive='true')}
#MathJax_ZoomOverlay {position: absolute; left: 0; top: 0; z-index: 300; display: inline-block; width: 100%; height: 100%; border: 0; padding: 0; margin: 0; background-color: white; opacity: 0; filter: alpha(opacity=0)}
#MathJax_ZoomFrame {position: relative; display: inline-block; height: 0; width: 0}
#MathJax_ZoomEventTrap {position: absolute; left: 0; top: 0; z-index: 302; display: inline-block; border: 0; padding: 0; margin: 0; background-color: white; opacity: 0; filter: alpha(opacity=0)}
</style><style type="text/css">.MathJax_Preview {color: #888}
#MathJax_Message {position: fixed; left: 1em; bottom: 1.5em; background-color: #E6E6E6; border: 1px solid #959595; margin: 0px; padding: 2px 8px; z-index: 102; color: black; font-size: 80%; width: auto; white-space: nowrap}
#MathJax_MSIE_Frame {position: absolute; top: 0; left: 0; width: 0px; z-index: 101; border: 0px; margin: 0px; padding: 0px}
.MathJax_Error {color: #CC0000; font-style: italic}
</style><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="custom/custom" src="./README_files/custom.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/plotlywidget/extension" src="./README_files/extension.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/jupyter-js-widgets/extension" src="./README_files/extension.js(1).download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/nbextensions_configurator/config_menu/main" src="./README_files/main.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/contrib_nbextensions_help_item/main" src="./README_files/main.js(1).download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/varInspector/main" src="./README_files/main.js(2).download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/code_prettify/code_prettify" src="./README_files/code_prettify.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/collapsible_headings/main" src="./README_files/main.js(3).download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/toc2/main" src="./README_files/main.js(4).download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/codefolding/main" src="./README_files/main.js(5).download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/export_embedded/main" src="./README_files/main.js(6).download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/code_prettify/autopep8" src="./README_files/autopep8.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/code_font_size/code_font_size" src="./README_files/code_font_size.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/gist_it/main" src="./README_files/main.js(7).download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/python-markdown/main" src="./README_files/main.js(8).download"></script><style type="text/css">div.MathJax_MathML {text-align: center; margin: .75em 0px; display: block!important}
.MathJax_MathML {font-style: normal; font-weight: normal; line-height: normal; font-size: 100%; font-size-adjust: none; text-indent: 0; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0; min-height: 0; border: 0; padding: 0; margin: 0}
span.MathJax_MathML {display: inline!important}
.MathJax_mmlExBox {display: block!important; overflow: hidden; height: 1px; width: 60ex; min-height: 0; max-height: none; padding: 0; border: 0; margin: 0}
[class="MJX-tex-oldstyle"] {font-family: MathJax_Caligraphic, MathJax_Caligraphic-WEB}
[class="MJX-tex-oldstyle-bold"] {font-family: MathJax_Caligraphic, MathJax_Caligraphic-WEB; font-weight: bold}
[class="MJX-tex-caligraphic"] {font-family: MathJax_Caligraphic, MathJax_Caligraphic-WEB}
[class="MJX-tex-caligraphic-bold"] {font-family: MathJax_Caligraphic, MathJax_Caligraphic-WEB; font-weight: bold}
@font-face /*1*/ {font-family: MathJax_Caligraphic-WEB; src: url('http://localhost:8888/static/components/MathJax/fonts/HTML-CSS/TeX/otf/MathJax_Caligraphic-Regular.otf')}
@font-face /*2*/ {font-family: MathJax_Caligraphic-WEB; font-weight: bold; src: url('http://localhost:8888/static/components/MathJax/fonts/HTML-CSS/TeX/otf/MathJax_Caligraphic-Bold.otf')}
[mathvariant="double-struck"] {font-family: MathJax_AMS, MathJax_AMS-WEB}
[mathvariant="script"] {font-family: MathJax_Script, MathJax_Script-WEB}
[mathvariant="fraktur"] {font-family: MathJax_Fraktur, MathJax_Fraktur-WEB}
[mathvariant="bold-script"] {font-family: MathJax_Script, MathJax_Caligraphic-WEB; font-weight: bold}
[mathvariant="bold-fraktur"] {font-family: MathJax_Fraktur, MathJax_Fraktur-WEB; font-weight: bold}
[mathvariant="monospace"] {font-family: monospace}
[mathvariant="sans-serif"] {font-family: sans-serif}
[mathvariant="bold-sans-serif"] {font-family: sans-serif; font-weight: bold}
[mathvariant="sans-serif-italic"] {font-family: sans-serif; font-style: italic}
[mathvariant="sans-serif-bold-italic"] {font-family: sans-serif; font-style: italic; font-weight: bold}
@font-face /*3*/ {font-family: MathJax_AMS-WEB; src: url('http://localhost:8888/static/components/MathJax/fonts/HTML-CSS/TeX/otf/MathJax_AMS-Regular.otf')}
@font-face /*4*/ {font-family: MathJax_Script-WEB; src: url('http://localhost:8888/static/components/MathJax/fonts/HTML-CSS/TeX/otf/MathJax_Script-Regular.otf')}
@font-face /*5*/ {font-family: MathJax_Fraktur-WEB; src: url('http://localhost:8888/static/components/MathJax/fonts/HTML-CSS/TeX/otf/MathJax_Fraktur-Regular.otf')}
@font-face /*6*/ {font-family: MathJax_Fraktur-WEB; font-weight: bold; src: url('http://localhost:8888/static/components/MathJax/fonts/HTML-CSS/TeX/otf/MathJax_Fraktur-Bold.otf')}
</style><style type="text/css">.MJXp-script {font-size: .8em}
.MJXp-right {-webkit-transform-origin: right; -moz-transform-origin: right; -ms-transform-origin: right; -o-transform-origin: right; transform-origin: right}
.MJXp-bold {font-weight: bold}
.MJXp-italic {font-style: italic}
.MJXp-scr {font-family: MathJax_Script,'Times New Roman',Times,STIXGeneral,serif}
.MJXp-frak {font-family: MathJax_Fraktur,'Times New Roman',Times,STIXGeneral,serif}
.MJXp-sf {font-family: MathJax_SansSerif,'Times New Roman',Times,STIXGeneral,serif}
.MJXp-cal {font-family: MathJax_Caligraphic,'Times New Roman',Times,STIXGeneral,serif}
.MJXp-mono {font-family: MathJax_Typewriter,'Times New Roman',Times,STIXGeneral,serif}
.MJXp-largeop {font-size: 150%}
.MJXp-largeop.MJXp-int {vertical-align: -.2em}
.MJXp-math {display: inline-block; line-height: 1.2; text-indent: 0; font-family: 'Times New Roman',Times,STIXGeneral,serif; white-space: nowrap; border-collapse: collapse}
.MJXp-display {display: block; text-align: center; margin: 1em 0}
.MJXp-math span {display: inline-block}
.MJXp-box {display: block!important; text-align: center}
.MJXp-box:after {content: " "}
.MJXp-rule {display: block!important; margin-top: .1em}
.MJXp-char {display: block!important}
.MJXp-mo {margin: 0 .15em}
.MJXp-mfrac {margin: 0 .125em; vertical-align: .25em}
.MJXp-denom {display: inline-table!important; width: 100%}
.MJXp-denom > * {display: table-row!important}
.MJXp-surd {vertical-align: top}
.MJXp-surd > * {display: block!important}
.MJXp-script-box > *  {display: table!important; height: 50%}
.MJXp-script-box > * > * {display: table-cell!important; vertical-align: top}
.MJXp-script-box > *:last-child > * {vertical-align: bottom}
.MJXp-script-box > * > * > * {display: block!important}
.MJXp-mphantom {visibility: hidden}
.MJXp-munderover {display: inline-table!important}
.MJXp-over {display: inline-block!important; text-align: center}
.MJXp-over > * {display: block!important}
.MJXp-munderover > * {display: table-row!important}
.MJXp-mtable {vertical-align: .25em; margin: 0 .125em}
.MJXp-mtable > * {display: inline-table!important; vertical-align: middle}
.MJXp-mtr {display: table-row!important}
.MJXp-mtd {display: table-cell!important; text-align: center; padding: .5em 0 0 .5em}
.MJXp-mtr > .MJXp-mtd:first-child {padding-left: 0}
.MJXp-mtr:first-child > .MJXp-mtd {padding-top: 0}
.MJXp-mlabeledtr {display: table-row!important}
.MJXp-mlabeledtr > .MJXp-mtd:first-child {padding-left: 0}
.MJXp-mlabeledtr:first-child > .MJXp-mtd {padding-top: 0}
.MJXp-merror {background-color: #FFFF88; color: #CC0000; border: 1px solid #CC0000; padding: 1px 3px; font-style: normal; font-size: 90%}
.MJXp-scale0 {-webkit-transform: scaleX(.0); -moz-transform: scaleX(.0); -ms-transform: scaleX(.0); -o-transform: scaleX(.0); transform: scaleX(.0)}
.MJXp-scale1 {-webkit-transform: scaleX(.1); -moz-transform: scaleX(.1); -ms-transform: scaleX(.1); -o-transform: scaleX(.1); transform: scaleX(.1)}
.MJXp-scale2 {-webkit-transform: scaleX(.2); -moz-transform: scaleX(.2); -ms-transform: scaleX(.2); -o-transform: scaleX(.2); transform: scaleX(.2)}
.MJXp-scale3 {-webkit-transform: scaleX(.3); -moz-transform: scaleX(.3); -ms-transform: scaleX(.3); -o-transform: scaleX(.3); transform: scaleX(.3)}
.MJXp-scale4 {-webkit-transform: scaleX(.4); -moz-transform: scaleX(.4); -ms-transform: scaleX(.4); -o-transform: scaleX(.4); transform: scaleX(.4)}
.MJXp-scale5 {-webkit-transform: scaleX(.5); -moz-transform: scaleX(.5); -ms-transform: scaleX(.5); -o-transform: scaleX(.5); transform: scaleX(.5)}
.MJXp-scale6 {-webkit-transform: scaleX(.6); -moz-transform: scaleX(.6); -ms-transform: scaleX(.6); -o-transform: scaleX(.6); transform: scaleX(.6)}
.MJXp-scale7 {-webkit-transform: scaleX(.7); -moz-transform: scaleX(.7); -ms-transform: scaleX(.7); -o-transform: scaleX(.7); transform: scaleX(.7)}
.MJXp-scale8 {-webkit-transform: scaleX(.8); -moz-transform: scaleX(.8); -ms-transform: scaleX(.8); -o-transform: scaleX(.8); transform: scaleX(.8)}
.MJXp-scale9 {-webkit-transform: scaleX(.9); -moz-transform: scaleX(.9); -ms-transform: scaleX(.9); -o-transform: scaleX(.9); transform: scaleX(.9)}
.MathJax_PHTML .noError {vertical-align: ; font-size: 90%; text-align: left; color: black; padding: 1px 3px; border: 1px solid}
</style><style type="text/css">.MathJax_Display {text-align: center; margin: 0; position: relative; display: block!important; text-indent: 0; max-width: none; max-height: none; min-width: 0; min-height: 0; width: 100%}
.MathJax .merror {background-color: #FFFF88; color: #CC0000; border: 1px solid #CC0000; padding: 1px 3px; font-style: normal; font-size: 90%}
.MathJax .MJX-monospace {font-family: monospace}
.MathJax .MJX-sans-serif {font-family: sans-serif}
#MathJax_Tooltip {background-color: InfoBackground; color: InfoText; border: 1px solid black; box-shadow: 2px 2px 5px #AAAAAA; -webkit-box-shadow: 2px 2px 5px #AAAAAA; -moz-box-shadow: 2px 2px 5px #AAAAAA; -khtml-box-shadow: 2px 2px 5px #AAAAAA; filter: progid:DXImageTransform.Microsoft.dropshadow(OffX=2, OffY=2, Color='gray', Positive='true'); padding: 3px 4px; z-index: 401; position: absolute; left: 0; top: 0; width: auto; height: auto; display: none}
.MathJax {display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 100%; font-size-adjust: none; text-indent: 0; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0; min-height: 0; border: 0; padding: 0; margin: 0}
.MathJax:focus, body :focus .MathJax {display: inline-table}
.MathJax.MathJax_FullWidth {text-align: center; display: table-cell!important; width: 10000em!important}
.MathJax img, .MathJax nobr, .MathJax a {border: 0; padding: 0; margin: 0; max-width: none; max-height: none; min-width: 0; min-height: 0; vertical-align: 0; line-height: normal; text-decoration: none}
img.MathJax_strut {border: 0!important; padding: 0!important; margin: 0!important; vertical-align: 0!important}
.MathJax span {display: inline; position: static; border: 0; padding: 0; margin: 0; vertical-align: 0; line-height: normal; text-decoration: none; box-sizing: content-box}
.MathJax nobr {white-space: nowrap!important}
.MathJax img {display: inline!important; float: none!important}
.MathJax * {transition: none; -webkit-transition: none; -moz-transition: none; -ms-transition: none; -o-transition: none}
.MathJax_Processing {visibility: hidden; position: fixed; width: 0; height: 0; overflow: hidden}
.MathJax_Processed {display: none!important}
.MathJax_ExBox {display: block!important; overflow: hidden; width: 1px; height: 60ex; min-height: 0; max-height: none}
.MathJax .MathJax_EmBox {display: block!important; overflow: hidden; width: 1px; height: 60em; min-height: 0; max-height: none}
.MathJax_LineBox {display: table!important}
.MathJax_LineBox span {display: table-cell!important; width: 10000em!important; min-width: 0; max-width: none; padding: 0; border: 0; margin: 0}
.MathJax .MathJax_HitBox {cursor: text; background: white; opacity: 0; filter: alpha(opacity=0)}
.MathJax .MathJax_HitBox * {filter: none; opacity: 1; background: transparent}
#MathJax_Tooltip * {filter: none; opacity: 1; background: transparent}
@font-face {font-family: MathJax_Blank; src: url('about:blank')}
.MathJax .noError {vertical-align: ; font-size: 90%; text-align: left; color: black; padding: 1px 3px; border: 1px solid}
</style><link type="text/css" rel="stylesheet" href="./README_files/main.css"><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/toc2/toc2" src="./README_files/toc2.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/code_prettify/kernel_exec_on_cell" src="./README_files/kernel_exec_on_cell.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="codemirror/addon/fold/foldcode" src="./README_files/foldcode.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="codemirror/addon/fold/foldgutter" src="./README_files/foldgutter.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="codemirror/addon/fold/brace-fold" src="./README_files/brace-fold.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="codemirror/addon/fold/indent-fold" src="./README_files/indent-fold.js.download"></script><link id="collapsible_headings_css" rel="stylesheet" type="text/css" href="./README_files/main(1).css"><link type="text/css" rel="stylesheet" href="./README_files/main(2).css"><style id="collapsible_headings_indent_css">.collapsible_headings_toggle .h1 { margin-right: 40px; }
.collapsible_headings_toggle .h2 { margin-right: 32px; }
.collapsible_headings_toggle .h3 { margin-right: 24px; }
.collapsible_headings_toggle .h4 { margin-right: 16px; }
.collapsible_headings_toggle .h5 { margin-right: 8px; }
.collapsible_headings_toggle .h6 { margin-right: 0px; }</style><link type="text/css" rel="stylesheet" href="./README_files/main(3).css"><link type="text/css" rel="stylesheet" href="./README_files/foldgutter.css"><link type="text/css" rel="stylesheet" href="./README_files/foldgutter(1).css"><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/codefolding/firstline-fold" src="./README_files/firstline-fold.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/codefolding/magic-fold" src="./README_files/magic-fold.js.download"></script><style type="text/css">/*
 * Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

/* Override the correction for the prompt area in https://github.com/jupyter/notebook/blob/dd41d9fd5c4f698bd7468612d877828a7eeb0e7a/IPython/html/static/notebook/less/outputarea.less#L110 */

.jupyter-widgets-output-area div.output_subarea {
    max-width: 100%;
}

/* Work-around for the bug fixed in https://github.com/jupyter/notebook/pull/2961 */

.jupyter-widgets-output-area > .out_prompt_overlay {
    display: none;
}
</style><style type="text/css">/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/
/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/
.p-Widget {
  -webkit-box-sizing: border-box;
          box-sizing: border-box;
  position: relative;
  overflow: hidden;
  cursor: default;
}
.p-Widget.p-mod-hidden {
  display: none !important;
}
/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/
.p-CommandPalette {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
      -ms-flex-direction: column;
          flex-direction: column;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
.p-CommandPalette-search {
  -webkit-box-flex: 0;
      -ms-flex: 0 0 auto;
          flex: 0 0 auto;
}
.p-CommandPalette-content {
  -webkit-box-flex: 1;
      -ms-flex: 1 1 auto;
          flex: 1 1 auto;
  margin: 0;
  padding: 0;
  min-height: 0;
  overflow: auto;
  list-style-type: none;
}
.p-CommandPalette-header {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}
.p-CommandPalette-item {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: horizontal;
  -webkit-box-direction: normal;
      -ms-flex-direction: row;
          flex-direction: row;
}
.p-CommandPalette-itemIcon {
  -webkit-box-flex: 0;
      -ms-flex: 0 0 auto;
          flex: 0 0 auto;
}
.p-CommandPalette-itemContent {
  -webkit-box-flex: 1;
      -ms-flex: 1 1 auto;
          flex: 1 1 auto;
}
.p-CommandPalette-itemShortcut {
  -webkit-box-flex: 0;
      -ms-flex: 0 0 auto;
          flex: 0 0 auto;
}
.p-CommandPalette-itemLabel {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}
/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/
.p-DockPanel {
  z-index: 0;
}
.p-DockPanel-widget {
  z-index: 0;
}
.p-DockPanel-tabBar {
  z-index: 1;
}
.p-DockPanel-handle {
  z-index: 2;
}
.p-DockPanel-handle.p-mod-hidden {
  display: none !important;
}
.p-DockPanel-handle:after {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  content: '';
}
.p-DockPanel-handle[data-orientation='horizontal'] {
  cursor: ew-resize;
}
.p-DockPanel-handle[data-orientation='vertical'] {
  cursor: ns-resize;
}
.p-DockPanel-handle[data-orientation='horizontal']:after {
  left: 50%;
  min-width: 8px;
  -webkit-transform: translateX(-50%);
          transform: translateX(-50%);
}
.p-DockPanel-handle[data-orientation='vertical']:after {
  top: 50%;
  min-height: 8px;
  -webkit-transform: translateY(-50%);
          transform: translateY(-50%);
}
.p-DockPanel-overlay {
  z-index: 3;
  -webkit-box-sizing: border-box;
          box-sizing: border-box;
  pointer-events: none;
}
.p-DockPanel-overlay.p-mod-hidden {
  display: none !important;
}
/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/
.p-Menu {
  z-index: 10000;
  position: absolute;
  white-space: nowrap;
  overflow-x: hidden;
  overflow-y: auto;
  outline: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
.p-Menu-content {
  margin: 0;
  padding: 0;
  display: table;
  list-style-type: none;
}
.p-Menu-item {
  display: table-row;
}
.p-Menu-item.p-mod-hidden,
.p-Menu-item.p-mod-collapsed {
  display: none !important;
}
.p-Menu-itemIcon,
.p-Menu-itemSubmenuIcon {
  display: table-cell;
  text-align: center;
}
.p-Menu-itemLabel {
  display: table-cell;
  text-align: left;
}
.p-Menu-itemShortcut {
  display: table-cell;
  text-align: right;
}
/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/
.p-MenuBar {
  outline: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
.p-MenuBar-content {
  margin: 0;
  padding: 0;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: horizontal;
  -webkit-box-direction: normal;
      -ms-flex-direction: row;
          flex-direction: row;
  list-style-type: none;
}
.p-MenuBar-item {
  -webkit-box-sizing: border-box;
          box-sizing: border-box;
}
.p-MenuBar-itemIcon,
.p-MenuBar-itemLabel {
  display: inline-block;
}
/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/
.p-ScrollBar {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
.p-ScrollBar[data-orientation='horizontal'] {
  -webkit-box-orient: horizontal;
  -webkit-box-direction: normal;
      -ms-flex-direction: row;
          flex-direction: row;
}
.p-ScrollBar[data-orientation='vertical'] {
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
      -ms-flex-direction: column;
          flex-direction: column;
}
.p-ScrollBar-button {
  -webkit-box-sizing: border-box;
          box-sizing: border-box;
  -webkit-box-flex: 0;
      -ms-flex: 0 0 auto;
          flex: 0 0 auto;
}
.p-ScrollBar-track {
  -webkit-box-sizing: border-box;
          box-sizing: border-box;
  position: relative;
  overflow: hidden;
  -webkit-box-flex: 1;
      -ms-flex: 1 1 auto;
          flex: 1 1 auto;
}
.p-ScrollBar-thumb {
  -webkit-box-sizing: border-box;
          box-sizing: border-box;
  position: absolute;
}
/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/
.p-SplitPanel-child {
  z-index: 0;
}
.p-SplitPanel-handle {
  z-index: 1;
}
.p-SplitPanel-handle.p-mod-hidden {
  display: none !important;
}
.p-SplitPanel-handle:after {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  content: '';
}
.p-SplitPanel[data-orientation='horizontal'] > .p-SplitPanel-handle {
  cursor: ew-resize;
}
.p-SplitPanel[data-orientation='vertical'] > .p-SplitPanel-handle {
  cursor: ns-resize;
}
.p-SplitPanel[data-orientation='horizontal'] > .p-SplitPanel-handle:after {
  left: 50%;
  min-width: 8px;
  -webkit-transform: translateX(-50%);
          transform: translateX(-50%);
}
.p-SplitPanel[data-orientation='vertical'] > .p-SplitPanel-handle:after {
  top: 50%;
  min-height: 8px;
  -webkit-transform: translateY(-50%);
          transform: translateY(-50%);
}
/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/
.p-TabBar {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
.p-TabBar[data-orientation='horizontal'] {
  -webkit-box-orient: horizontal;
  -webkit-box-direction: normal;
      -ms-flex-direction: row;
          flex-direction: row;
}
.p-TabBar[data-orientation='vertical'] {
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
      -ms-flex-direction: column;
          flex-direction: column;
}
.p-TabBar-content {
  margin: 0;
  padding: 0;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-flex: 1;
      -ms-flex: 1 1 auto;
          flex: 1 1 auto;
  list-style-type: none;
}
.p-TabBar[data-orientation='horizontal'] > .p-TabBar-content {
  -webkit-box-orient: horizontal;
  -webkit-box-direction: normal;
      -ms-flex-direction: row;
          flex-direction: row;
}
.p-TabBar[data-orientation='vertical'] > .p-TabBar-content {
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
      -ms-flex-direction: column;
          flex-direction: column;
}
.p-TabBar-tab {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: horizontal;
  -webkit-box-direction: normal;
      -ms-flex-direction: row;
          flex-direction: row;
  -webkit-box-sizing: border-box;
          box-sizing: border-box;
  overflow: hidden;
}
.p-TabBar-tabIcon,
.p-TabBar-tabCloseIcon {
  -webkit-box-flex: 0;
      -ms-flex: 0 0 auto;
          flex: 0 0 auto;
}
.p-TabBar-tabLabel {
  -webkit-box-flex: 1;
      -ms-flex: 1 1 auto;
          flex: 1 1 auto;
  overflow: hidden;
  white-space: nowrap;
}
.p-TabBar-tab.p-mod-hidden {
  display: none !important;
}
.p-TabBar.p-mod-dragging .p-TabBar-tab {
  position: relative;
}
.p-TabBar.p-mod-dragging[data-orientation='horizontal'] .p-TabBar-tab {
  left: 0;
  -webkit-transition: left 150ms ease;
  transition: left 150ms ease;
}
.p-TabBar.p-mod-dragging[data-orientation='vertical'] .p-TabBar-tab {
  top: 0;
  -webkit-transition: top 150ms ease;
  transition: top 150ms ease;
}
.p-TabBar.p-mod-dragging .p-TabBar-tab.p-mod-dragging {
  -webkit-transition: none;
  transition: none;
}
/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/
.p-TabPanel-tabBar {
  z-index: 1;
}
.p-TabPanel-stackedPanel {
  z-index: 0;
}
</style><style type="text/css">/* Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

 .jupyter-widgets-disconnected::before {
    content: "\F127"; /* chain-broken */
    display: inline-block;
    font: normal normal normal 14px/1 FontAwesome;
    font-size: inherit;
    text-rendering: auto;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #d9534f;
    padding: 3px;
    -ms-flex-item-align: start;
        align-self: flex-start;
}
</style><style type="text/css">/* Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

 /* We import all of these together in a single css file because the Webpack
loader sees only one file at a time. This allows postcss to see the variable
definitions when they are used. */

 /*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

 /*
This file is copied from the JupyterLab project to define default styling for
when the widget styling is compiled down to eliminate CSS variables. We make one
change - we comment out the font import below.
*/

 /**
 * The material design colors are adapted from google-material-color v1.2.6
 * https://github.com/danlevan/google-material-color
 * https://github.com/danlevan/google-material-color/blob/f67ca5f4028b2f1b34862f64b0ca67323f91b088/dist/palette.var.css
 *
 * The license for the material design color CSS variables is as follows (see
 * https://github.com/danlevan/google-material-color/blob/f67ca5f4028b2f1b34862f64b0ca67323f91b088/LICENSE)
 *
 * The MIT License (MIT)
 *
 * Copyright (c) 2014 Dan Le Van
 *
 * Permission is hereby granted, free of charge, to any person obtaining a copy
 * of this software and associated documentation files (the "Software"), to deal
 * in the Software without restriction, including without limitation the rights
 * to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
 * copies of the Software, and to permit persons to whom the Software is
 * furnished to do so, subject to the following conditions:
 *
 * The above copyright notice and this permission notice shall be included in
 * all copies or substantial portions of the Software.
 *
 * THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
 * IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
 * FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
 * AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
 * LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
 * OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
 * SOFTWARE.
 */

 /*
The following CSS variables define the main, public API for styling JupyterLab.
These variables should be used by all plugins wherever possible. In other
words, plugins should not define custom colors, sizes, etc unless absolutely
necessary. This enables users to change the visual theme of JupyterLab
by changing these variables.

Many variables appear in an ordered sequence (0,1,2,3). These sequences
are designed to work well together, so for example, `--jp-border-color1` should
be used with `--jp-layout-color1`. The numbers have the following meanings:

* 0: super-primary, reserved for special emphasis
* 1: primary, most important under normal situations
* 2: secondary, next most important under normal situations
* 3: tertiary, next most important under normal situations

Throughout JupyterLab, we are mostly following principles from Google's
Material Design when selecting colors. We are not, however, following
all of MD as it is not optimized for dense, information rich UIs.
*/

 /*
 * Optional monospace font for input/output prompt.
 */

 /* Commented out in ipywidgets since we don't need it. */

 /* @import url('https://fonts.googleapis.com/css?family=Roboto+Mono'); */

 /*
 * Added for compabitility with output area
 */

 :root {

  /* Borders

  The following variables, specify the visual styling of borders in JupyterLab.
   */

  /* UI Fonts

  The UI font CSS variables are used for the typography all of the JupyterLab
  user interface elements that are not directly user generated content.
  */ /* Base font size */ /* Ensures px perfect FontAwesome icons */

  /* Use these font colors against the corresponding main layout colors.
     In a light theme, these go from dark to light.
  */

  /* Use these against the brand/accent/warn/error colors.
     These will typically go from light to darker, in both a dark and light theme
   */

  /* Content Fonts

  Content font variables are used for typography of user generated content.
  */ /* Base font size */


  /* Layout

  The following are the main layout colors use in JupyterLab. In a light
  theme these would go from light to dark.
  */

  /* Brand/accent */

  /* State colors (warn, error, success, info) */

  /* Cell specific styles */
  /* A custom blend of MD grey and blue 600
   * See https://meyerweb.com/eric/tools/color-blend/#546E7A:1E88E5:5:hex */
  /* A custom blend of MD grey and orange 600
   * https://meyerweb.com/eric/tools/color-blend/#546E7A:F4511E:5:hex */

  /* Notebook specific styles */

  /* Console specific styles */

  /* Toolbar specific styles */
}

 /* Copyright (c) Jupyter Development Team.
 * Distributed under the terms of the Modified BSD License.
 */

 /*
 * We assume that the CSS variables in
 * https://github.com/jupyterlab/jupyterlab/blob/master/src/default-theme/variables.css
 * have been defined.
 */

 /* This file has code derived from PhosphorJS CSS files, as noted below. The license for this PhosphorJS code is:

Copyright (c) 2014-2017, PhosphorJS Contributors
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

* Redistributions of source code must retain the above copyright notice, this
  list of conditions and the following disclaimer.

* Redistributions in binary form must reproduce the above copyright notice,
  this list of conditions and the following disclaimer in the documentation
  and/or other materials provided with the distribution.

* Neither the name of the copyright holder nor the names of its
  contributors may be used to endorse or promote products derived from
  this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

*/

 /*
 * The following section is derived from https://github.com/phosphorjs/phosphor/blob/23b9d075ebc5b73ab148b6ebfc20af97f85714c4/packages/widgets/style/tabbar.css 
 * We've scoped the rules so that they are consistent with exactly our code.
 */

 .jupyter-widgets.widget-tab > .p-TabBar {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

 .jupyter-widgets.widget-tab > .p-TabBar[data-orientation='horizontal'] {
  -webkit-box-orient: horizontal;
  -webkit-box-direction: normal;
      -ms-flex-direction: row;
          flex-direction: row;
}

 .jupyter-widgets.widget-tab > .p-TabBar[data-orientation='vertical'] {
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
      -ms-flex-direction: column;
          flex-direction: column;
}

 .jupyter-widgets.widget-tab > .p-TabBar > .p-TabBar-content {
  margin: 0;
  padding: 0;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-flex: 1;
      -ms-flex: 1 1 auto;
          flex: 1 1 auto;
  list-style-type: none;
}

 .jupyter-widgets.widget-tab > .p-TabBar[data-orientation='horizontal'] > .p-TabBar-content {
  -webkit-box-orient: horizontal;
  -webkit-box-direction: normal;
      -ms-flex-direction: row;
          flex-direction: row;
}

 .jupyter-widgets.widget-tab > .p-TabBar[data-orientation='vertical'] > .p-TabBar-content {
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
      -ms-flex-direction: column;
          flex-direction: column;
}

 .jupyter-widgets.widget-tab > .p-TabBar .p-TabBar-tab {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: horizontal;
  -webkit-box-direction: normal;
      -ms-flex-direction: row;
          flex-direction: row;
  -webkit-box-sizing: border-box;
          box-sizing: border-box;
  overflow: hidden;
}

 .jupyter-widgets.widget-tab > .p-TabBar .p-TabBar-tabIcon,
.jupyter-widgets.widget-tab > .p-TabBar .p-TabBar-tabCloseIcon {
  -webkit-box-flex: 0;
      -ms-flex: 0 0 auto;
          flex: 0 0 auto;
}

 .jupyter-widgets.widget-tab > .p-TabBar .p-TabBar-tabLabel {
  -webkit-box-flex: 1;
      -ms-flex: 1 1 auto;
          flex: 1 1 auto;
  overflow: hidden;
  white-space: nowrap;
}

 .jupyter-widgets.widget-tab > .p-TabBar .p-TabBar-tab.p-mod-hidden {
  display: none !important;
}

 .jupyter-widgets.widget-tab > .p-TabBar.p-mod-dragging .p-TabBar-tab {
  position: relative;
}

 .jupyter-widgets.widget-tab > .p-TabBar.p-mod-dragging[data-orientation='horizontal'] .p-TabBar-tab {
  left: 0;
  -webkit-transition: left 150ms ease;
  transition: left 150ms ease;
}

 .jupyter-widgets.widget-tab > .p-TabBar.p-mod-dragging[data-orientation='vertical'] .p-TabBar-tab {
  top: 0;
  -webkit-transition: top 150ms ease;
  transition: top 150ms ease;
}

 .jupyter-widgets.widget-tab > .p-TabBar.p-mod-dragging .p-TabBar-tab.p-mod-dragging {
  -webkit-transition: none;
  transition: none;
}

 /* End tabbar.css */

 :root { /* margin between inline elements */

    /* From Material Design Lite */
}

 .jupyter-widgets {
    margin: 2px;
    -webkit-box-sizing: border-box;
            box-sizing: border-box;
    color: black;
    overflow: visible;
}

 .jupyter-widgets.jupyter-widgets-disconnected::before {
    line-height: 28px;
    height: 28px;
}

 .jp-Output-result > .jupyter-widgets {
    margin-left: 0;
    margin-right: 0;
}

 /* vbox and hbox */

 .widget-inline-hbox {
    /* Horizontal widgets */
    -webkit-box-sizing: border-box;
            box-sizing: border-box;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-orient: horizontal;
    -webkit-box-direction: normal;
        -ms-flex-direction: row;
            flex-direction: row;
    -webkit-box-align: baseline;
        -ms-flex-align: baseline;
            align-items: baseline;
}

 .widget-inline-vbox {
    /* Vertical Widgets */
    -webkit-box-sizing: border-box;
            box-sizing: border-box;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-orient: vertical;
    -webkit-box-direction: normal;
        -ms-flex-direction: column;
            flex-direction: column;
    -webkit-box-align: center;
        -ms-flex-align: center;
            align-items: center;
}

 .widget-box {
    -webkit-box-sizing: border-box;
            box-sizing: border-box;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    margin: 0;
    overflow: auto;
}

 .widget-gridbox {
    -webkit-box-sizing: border-box;
            box-sizing: border-box;
    display: grid;
    margin: 0;
    overflow: auto;
}

 .widget-hbox {
    -webkit-box-orient: horizontal;
    -webkit-box-direction: normal;
        -ms-flex-direction: row;
            flex-direction: row;
}

 .widget-vbox {
    -webkit-box-orient: vertical;
    -webkit-box-direction: normal;
        -ms-flex-direction: column;
            flex-direction: column;
}

 /* General Button Styling */

 .jupyter-button {
    padding-left: 10px;
    padding-right: 10px;
    padding-top: 0px;
    padding-bottom: 0px;
    display: inline-block;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    text-align: center;
    font-size: 13px;
    cursor: pointer;

    height: 28px;
    border: 0px solid;
    line-height: 28px;
    -webkit-box-shadow: none;
            box-shadow: none;

    color: rgba(0, 0, 0, .8);
    background-color: #EEEEEE;
    border-color: #E0E0E0;
    border: none;
}

 .jupyter-button i.fa {
    margin-right: 4px;
    pointer-events: none;
}

 .jupyter-button:empty:before {
    content: "\200B"; /* zero-width space */
}

 .jupyter-widgets.jupyter-button:disabled {
    opacity: 0.6;
}

 .jupyter-button i.fa.center {
    margin-right: 0;
}

 .jupyter-button:hover:enabled, .jupyter-button:focus:enabled {
    /* MD Lite 2dp shadow */
    -webkit-box-shadow: 0 2px 2px 0 rgba(0, 0, 0, .14),
                0 3px 1px -2px rgba(0, 0, 0, .2),
                0 1px 5px 0 rgba(0, 0, 0, .12);
            box-shadow: 0 2px 2px 0 rgba(0, 0, 0, .14),
                0 3px 1px -2px rgba(0, 0, 0, .2),
                0 1px 5px 0 rgba(0, 0, 0, .12);
}

 .jupyter-button:active, .jupyter-button.mod-active {
    /* MD Lite 4dp shadow */
    -webkit-box-shadow: 0 4px 5px 0 rgba(0, 0, 0, .14),
                0 1px 10px 0 rgba(0, 0, 0, .12),
                0 2px 4px -1px rgba(0, 0, 0, .2);
            box-shadow: 0 4px 5px 0 rgba(0, 0, 0, .14),
                0 1px 10px 0 rgba(0, 0, 0, .12),
                0 2px 4px -1px rgba(0, 0, 0, .2);
    color: rgba(0, 0, 0, .8);
    background-color: #BDBDBD;
}

 .jupyter-button:focus:enabled {
    outline: 1px solid #64B5F6;
}

 /* Button "Primary" Styling */

 .jupyter-button.mod-primary {
    color: rgba(255, 255, 255, 1.0);
    background-color: #2196F3;
}

 .jupyter-button.mod-primary.mod-active {
    color: rgba(255, 255, 255, 1);
    background-color: #1976D2;
}

 .jupyter-button.mod-primary:active {
    color: rgba(255, 255, 255, 1);
    background-color: #1976D2;
}

 /* Button "Success" Styling */

 .jupyter-button.mod-success {
    color: rgba(255, 255, 255, 1.0);
    background-color: #4CAF50;
}

 .jupyter-button.mod-success.mod-active {
    color: rgba(255, 255, 255, 1);
    background-color: #388E3C;
 }

 .jupyter-button.mod-success:active {
    color: rgba(255, 255, 255, 1);
    background-color: #388E3C;
 }

 /* Button "Info" Styling */

 .jupyter-button.mod-info {
    color: rgba(255, 255, 255, 1.0);
    background-color: #00BCD4;
}

 .jupyter-button.mod-info.mod-active {
    color: rgba(255, 255, 255, 1);
    background-color: #0097A7;
}

 .jupyter-button.mod-info:active {
    color: rgba(255, 255, 255, 1);
    background-color: #0097A7;
}

 /* Button "Warning" Styling */

 .jupyter-button.mod-warning {
    color: rgba(255, 255, 255, 1.0);
    background-color: #FF9800;
}

 .jupyter-button.mod-warning.mod-active {
    color: rgba(255, 255, 255, 1);
    background-color: #F57C00;
}

 .jupyter-button.mod-warning:active {
    color: rgba(255, 255, 255, 1);
    background-color: #F57C00;
}

 /* Button "Danger" Styling */

 .jupyter-button.mod-danger {
    color: rgba(255, 255, 255, 1.0);
    background-color: #F44336;
}

 .jupyter-button.mod-danger.mod-active {
    color: rgba(255, 255, 255, 1);
    background-color: #D32F2F;
}

 .jupyter-button.mod-danger:active {
    color: rgba(255, 255, 255, 1);
    background-color: #D32F2F;
}

 /* Widget Button*/

 .widget-button, .widget-toggle-button {
    width: 148px;
}

 /* Widget Label Styling */

 /* Override Bootstrap label css */

 .jupyter-widgets label {
    margin-bottom: 0;
    margin-bottom: initial;
}

 .widget-label-basic {
    /* Basic Label */
    color: black;
    font-size: 13px;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    line-height: 28px;
}

 .widget-label {
    /* Label */
    color: black;
    font-size: 13px;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    line-height: 28px;
}

 .widget-inline-hbox .widget-label {
    /* Horizontal Widget Label */
    color: black;
    text-align: right;
    margin-right: 8px;
    width: 80px;
    -ms-flex-negative: 0;
        flex-shrink: 0;
}

 .widget-inline-vbox .widget-label {
    /* Vertical Widget Label */
    color: black;
    text-align: center;
    line-height: 28px;
}

 /* Widget Readout Styling */

 .widget-readout {
    color: black;
    font-size: 13px;
    height: 28px;
    line-height: 28px;
    overflow: hidden;
    white-space: nowrap;
    text-align: center;
}

 .widget-readout.overflow {
    /* Overflowing Readout */

    /* From Material Design Lite
        shadow-key-umbra-opacity: 0.2;
        shadow-key-penumbra-opacity: 0.14;
        shadow-ambient-shadow-opacity: 0.12;
     */
    -webkit-box-shadow: 0 2px 2px 0 rgba(0, 0, 0, .2),
                        0 3px 1px -2px rgba(0, 0, 0, .14),
                        0 1px 5px 0 rgba(0, 0, 0, .12);

    box-shadow: 0 2px 2px 0 rgba(0, 0, 0, .2),
                0 3px 1px -2px rgba(0, 0, 0, .14),
                0 1px 5px 0 rgba(0, 0, 0, .12);
}

 .widget-inline-hbox .widget-readout {
    /* Horizontal Readout */
    text-align: center;
    max-width: 148px;
    min-width: 72px;
    margin-left: 4px;
}

 .widget-inline-vbox .widget-readout {
    /* Vertical Readout */
    margin-top: 4px;
    /* as wide as the widget */
    width: inherit;
}

 /* Widget Checkbox Styling */

 .widget-checkbox {
    width: 300px;
    height: 28px;
    line-height: 28px;
}

 .widget-checkbox input[type="checkbox"] {
    margin: 0px 8px 0px 0px;
    line-height: 28px;
    font-size: large;
    -webkit-box-flex: 1;
        -ms-flex-positive: 1;
            flex-grow: 1;
    -ms-flex-negative: 0;
        flex-shrink: 0;
    -ms-flex-item-align: center;
        align-self: center;
}

 /* Widget Valid Styling */

 .widget-valid {
    height: 28px;
    line-height: 28px;
    width: 148px;
    font-size: 13px;
}

 .widget-valid i:before {
    line-height: 28px;
    margin-right: 4px;
    margin-left: 4px;

    /* from the fa class in FontAwesome: https://github.com/FortAwesome/Font-Awesome/blob/49100c7c3a7b58d50baa71efef11af41a66b03d3/css/font-awesome.css#L14 */
    display: inline-block;
    font: normal normal normal 14px/1 FontAwesome;
    font-size: inherit;
    text-rendering: auto;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}

 .widget-valid.mod-valid i:before {
    content: "\F00C";
    color: green;
}

 .widget-valid.mod-invalid i:before {
    content: "\F00D";
    color: red;
}

 .widget-valid.mod-valid .widget-valid-readout {
    display: none;
}

 /* Widget Text and TextArea Stying */

 .widget-textarea, .widget-text {
    width: 300px;
}

 .widget-text input[type="text"], .widget-text input[type="number"]{
    height: 28px;
    line-height: 28px;
}

 .widget-text input[type="text"]:disabled, .widget-text input[type="number"]:disabled, .widget-textarea textarea:disabled {
    opacity: 0.6;
}

 .widget-text input[type="text"], .widget-text input[type="number"], .widget-textarea textarea {
    -webkit-box-sizing: border-box;
            box-sizing: border-box;
    border: 1px solid #9E9E9E;
    background-color: white;
    color: rgba(0, 0, 0, .8);
    font-size: 13px;
    padding: 4px 8px;
    -webkit-box-flex: 1;
        -ms-flex-positive: 1;
            flex-grow: 1;
    min-width: 0; /* This makes it possible for the flexbox to shrink this input */
    -ms-flex-negative: 1;
        flex-shrink: 1;
    outline: none !important;
}

 .widget-textarea textarea {
    height: inherit;
    width: inherit;
}

 .widget-text input:focus, .widget-textarea textarea:focus {
    border-color: #64B5F6;
}

 /* Widget Slider */

 .widget-slider .ui-slider {
    /* Slider Track */
    border: 1px solid #BDBDBD;
    background: #BDBDBD;
    -webkit-box-sizing: border-box;
            box-sizing: border-box;
    position: relative;
    border-radius: 0px;
}

 .widget-slider .ui-slider .ui-slider-handle {
    /* Slider Handle */
    outline: none !important; /* focused slider handles are colored - see below */
    position: absolute;
    background-color: white;
    border: 1px solid #9E9E9E;
    -webkit-box-sizing: border-box;
            box-sizing: border-box;
    z-index: 1;
    background-image: none; /* Override jquery-ui */
}

 /* Override jquery-ui */

 .widget-slider .ui-slider .ui-slider-handle:hover, .widget-slider .ui-slider .ui-slider-handle:focus {
    background-color: #2196F3;
    border: 1px solid #2196F3;
}

 .widget-slider .ui-slider .ui-slider-handle:active {
    background-color: #2196F3;
    border-color: #2196F3;
    z-index: 2;
    -webkit-transform: scale(1.2);
            transform: scale(1.2);
}

 .widget-slider  .ui-slider .ui-slider-range {
    /* Interval between the two specified value of a double slider */
    position: absolute;
    background: #2196F3;
    z-index: 0;
}

 /* Shapes of Slider Handles */

 .widget-hslider .ui-slider .ui-slider-handle {
    width: 16px;
    height: 16px;
    margin-top: -7px;
    margin-left: -7px;
    border-radius: 50%;
    top: 0;
}

 .widget-vslider .ui-slider .ui-slider-handle {
    width: 16px;
    height: 16px;
    margin-bottom: -7px;
    margin-left: -7px;
    border-radius: 50%;
    left: 0;
}

 .widget-hslider .ui-slider .ui-slider-range {
    height: 8px;
    margin-top: -3px;
}

 .widget-vslider .ui-slider .ui-slider-range {
    width: 8px;
    margin-left: -3px;
}

 /* Horizontal Slider */

 .widget-hslider {
    width: 300px;
    height: 28px;
    line-height: 28px;

    /* Override the align-items baseline. This way, the description and readout
    still seem to align their baseline properly, and we don't have to have
    align-self: stretch in the .slider-container. */
    -webkit-box-align: center;
        -ms-flex-align: center;
            align-items: center;
}

 .widgets-slider .slider-container {
    overflow: visible;
}

 .widget-hslider .slider-container {
    height: 28px;
    margin-left: 6px;
    margin-right: 6px;
    -webkit-box-flex: 1;
        -ms-flex: 1 1 148px;
            flex: 1 1 148px;
}

 .widget-hslider .ui-slider {
    /* Inner, invisible slide div */
    height: 4px;
    margin-top: 12px;
    width: 100%;
}

 /* Vertical Slider */

 .widget-vbox .widget-label {
    height: 28px;
    line-height: 28px;
}

 .widget-vslider {
    /* Vertical Slider */
    height: 200px;
    width: 72px;
}

 .widget-vslider .slider-container {
    -webkit-box-flex: 1;
        -ms-flex: 1 1 148px;
            flex: 1 1 148px;
    margin-left: auto;
    margin-right: auto;
    margin-bottom: 6px;
    margin-top: 6px;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-orient: vertical;
    -webkit-box-direction: normal;
        -ms-flex-direction: column;
            flex-direction: column;
}

 .widget-vslider .ui-slider-vertical {
    /* Inner, invisible slide div */
    width: 4px;
    -webkit-box-flex: 1;
        -ms-flex-positive: 1;
            flex-grow: 1;
    margin-left: auto;
    margin-right: auto;
}

 /* Widget Progress Styling */

 .progress-bar {
    -webkit-transition: none;
    transition: none;
}

 .progress-bar {
    height: 28px;
}

 .progress-bar {
    background-color: #2196F3;
}

 .progress-bar-success {
    background-color: #4CAF50;
}

 .progress-bar-info {
    background-color: #00BCD4;
}

 .progress-bar-warning {
    background-color: #FF9800;
}

 .progress-bar-danger {
    background-color: #F44336;
}

 .progress {
    background-color: #EEEEEE;
    border: none;
    -webkit-box-shadow: none;
            box-shadow: none;
}

 /* Horisontal Progress */

 .widget-hprogress {
    /* Progress Bar */
    height: 28px;
    line-height: 28px;
    width: 300px;
    -webkit-box-align: center;
        -ms-flex-align: center;
            align-items: center;

}

 .widget-hprogress .progress {
    -webkit-box-flex: 1;
        -ms-flex-positive: 1;
            flex-grow: 1;
    margin-top: 4px;
    margin-bottom: 4px;
    -ms-flex-item-align: stretch;
        align-self: stretch;
    /* Override bootstrap style */
    height: auto;
    height: initial;
}

 /* Vertical Progress */

 .widget-vprogress {
    height: 200px;
    width: 72px;
}

 .widget-vprogress .progress {
    -webkit-box-flex: 1;
        -ms-flex-positive: 1;
            flex-grow: 1;
    width: 20px;
    margin-left: auto;
    margin-right: auto;
    margin-bottom: 0;
}

 /* Select Widget Styling */

 .widget-dropdown {
    height: 28px;
    width: 300px;
    line-height: 28px;
}

 .widget-dropdown > select {
    padding-right: 20px;
    border: 1px solid #9E9E9E;
    border-radius: 0;
    height: inherit;
    -webkit-box-flex: 1;
        -ms-flex: 1 1 148px;
            flex: 1 1 148px;
    min-width: 0; /* This makes it possible for the flexbox to shrink this input */
    -webkit-box-sizing: border-box;
            box-sizing: border-box;
    outline: none !important;
    -webkit-box-shadow: none;
            box-shadow: none;
    background-color: white;
    color: rgba(0, 0, 0, .8);
    font-size: 13px;
    vertical-align: top;
    padding-left: 8px;
	appearance: none;
	-webkit-appearance: none;
	-moz-appearance: none;
    background-repeat: no-repeat;
	background-size: 20px;
	background-position: right center;
    background-image: url("data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4KPCEtLSBHZW5lcmF0b3I6IEFkb2JlIElsbHVzdHJhdG9yIDE5LjIuMSwgU1ZHIEV4cG9ydCBQbHVnLUluIC4gU1ZHIFZlcnNpb246IDYuMDAgQnVpbGQgMCkgIC0tPgo8c3ZnIHZlcnNpb249IjEuMSIgaWQ9IkxheWVyXzEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6eGxpbms9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkveGxpbmsiIHg9IjBweCIgeT0iMHB4IgoJIHZpZXdCb3g9IjAgMCAxOCAxOCIgc3R5bGU9ImVuYWJsZS1iYWNrZ3JvdW5kOm5ldyAwIDAgMTggMTg7IiB4bWw6c3BhY2U9InByZXNlcnZlIj4KPHN0eWxlIHR5cGU9InRleHQvY3NzIj4KCS5zdDB7ZmlsbDpub25lO30KPC9zdHlsZT4KPHBhdGggZD0iTTUuMiw1LjlMOSw5LjdsMy44LTMuOGwxLjIsMS4ybC00LjksNWwtNC45LTVMNS4yLDUuOXoiLz4KPHBhdGggY2xhc3M9InN0MCIgZD0iTTAtMC42aDE4djE4SDBWLTAuNnoiLz4KPC9zdmc+Cg");
}

 .widget-dropdown > select:focus {
    border-color: #64B5F6;
}

 .widget-dropdown > select:disabled {
    opacity: 0.6;
}

 /* To disable the dotted border in Firefox around select controls.
   See http://stackoverflow.com/a/18853002 */

 .widget-dropdown > select:-moz-focusring {
    color: transparent;
    text-shadow: 0 0 0 #000;
}

 /* Select and SelectMultiple */

 .widget-select {
    width: 300px;
    line-height: 28px;

    /* Because Firefox defines the baseline of a select as the bottom of the
    control, we align the entire control to the top and add padding to the
    select to get an approximate first line baseline alignment. */
    -webkit-box-align: start;
        -ms-flex-align: start;
            align-items: flex-start;
}

 .widget-select > select {
    border: 1px solid #9E9E9E;
    background-color: white;
    color: rgba(0, 0, 0, .8);
    font-size: 13px;
    -webkit-box-flex: 1;
        -ms-flex: 1 1 148px;
            flex: 1 1 148px;
    outline: none !important;
    overflow: auto;
    height: inherit;

    /* Because Firefox defines the baseline of a select as the bottom of the
    control, we align the entire control to the top and add padding to the
    select to get an approximate first line baseline alignment. */
    padding-top: 5px;
}

 .widget-select > select:focus {
    border-color: #64B5F6;
}

 .wiget-select > select > option {
    padding-left: 4px;
    line-height: 28px;
    /* line-height doesn't work on some browsers for select options */
    padding-top: calc(28px - var(--jp-widgets-font-size) / 2);
    padding-bottom: calc(28px - var(--jp-widgets-font-size) / 2);
}

 /* Toggle Buttons Styling */

 .widget-toggle-buttons {
    line-height: 28px;
}

 .widget-toggle-buttons .widget-toggle-button {
    margin-left: 2px;
    margin-right: 2px;
}

 .widget-toggle-buttons .jupyter-button:disabled {
    opacity: 0.6;
}

 /* Radio Buttons Styling */

 .widget-radio {
    width: 300px;
    line-height: 28px;
}

 .widget-radio-box {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-orient: vertical;
    -webkit-box-direction: normal;
        -ms-flex-direction: column;
            flex-direction: column;
    -webkit-box-align: stretch;
        -ms-flex-align: stretch;
            align-items: stretch;
    -webkit-box-sizing: border-box;
            box-sizing: border-box;
    -webkit-box-flex: 1;
        -ms-flex-positive: 1;
            flex-grow: 1;
    margin-bottom: 8px;
}

 .widget-radio-box label {
    height: 20px;
    line-height: 20px;
    font-size: 13px;
}

 .widget-radio-box input {
    height: 20px;
    line-height: 20px;
    margin: 0 8px 0 1px;
    float: left;
}

 /* Color Picker Styling */

 .widget-colorpicker {
    width: 300px;
    height: 28px;
    line-height: 28px;
}

 .widget-colorpicker > .widget-colorpicker-input {
    -webkit-box-flex: 1;
        -ms-flex-positive: 1;
            flex-grow: 1;
    -ms-flex-negative: 1;
        flex-shrink: 1;
    min-width: 72px;
}

 .widget-colorpicker input[type="color"] {
    width: 28px;
    height: 28px;
    padding: 0 2px; /* make the color square actually square on Chrome on OS X */
    background: white;
    color: rgba(0, 0, 0, .8);
    border: 1px solid #9E9E9E;
    border-left: none;
    -webkit-box-flex: 0;
        -ms-flex-positive: 0;
            flex-grow: 0;
    -ms-flex-negative: 0;
        flex-shrink: 0;
    -webkit-box-sizing: border-box;
            box-sizing: border-box;
    -ms-flex-item-align: stretch;
        align-self: stretch;
    outline: none !important;
}

 .widget-colorpicker.concise input[type="color"] {
    border-left: 1px solid #9E9E9E;
}

 .widget-colorpicker input[type="color"]:focus, .widget-colorpicker input[type="text"]:focus {
    border-color: #64B5F6;
}

 .widget-colorpicker input[type="text"] {
    -webkit-box-flex: 1;
        -ms-flex-positive: 1;
            flex-grow: 1;
    outline: none !important;
    height: 28px;
    line-height: 28px;
    background: white;
    color: rgba(0, 0, 0, .8);
    border: 1px solid #9E9E9E;
    font-size: 13px;
    padding: 4px 8px;
    min-width: 0; /* This makes it possible for the flexbox to shrink this input */
    -ms-flex-negative: 1;
        flex-shrink: 1;
    -webkit-box-sizing: border-box;
            box-sizing: border-box;
}

 .widget-colorpicker input[type="text"]:disabled {
    opacity: 0.6;
}

 /* Date Picker Styling */

 .widget-datepicker {
    width: 300px;
    height: 28px;
    line-height: 28px;
}

 .widget-datepicker input[type="date"] {
    -webkit-box-flex: 1;
        -ms-flex-positive: 1;
            flex-grow: 1;
    -ms-flex-negative: 1;
        flex-shrink: 1;
    min-width: 0; /* This makes it possible for the flexbox to shrink this input */
    outline: none !important;
    height: 28px;
    border: 1px solid #9E9E9E;
    background-color: white;
    color: rgba(0, 0, 0, .8);
    font-size: 13px;
    padding: 4px 8px;
    -webkit-box-sizing: border-box;
            box-sizing: border-box;
}

 .widget-datepicker input[type="date"]:focus {
    border-color: #64B5F6;
}

 .widget-datepicker input[type="date"]:invalid {
    border-color: #FF9800;
}

 .widget-datepicker input[type="date"]:disabled {
    opacity: 0.6;
}

 /* Play Widget */

 .widget-play {
    width: 148px;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-align: stretch;
        -ms-flex-align: stretch;
            align-items: stretch;
}

 .widget-play .jupyter-button {
    -webkit-box-flex: 1;
        -ms-flex-positive: 1;
            flex-grow: 1;
    height: auto;
}

 .widget-play .jupyter-button:disabled {
    opacity: 0.6;
}

 /* Tab Widget */

 .jupyter-widgets.widget-tab {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-orient: vertical;
    -webkit-box-direction: normal;
        -ms-flex-direction: column;
            flex-direction: column;
}

 .jupyter-widgets.widget-tab > .p-TabBar {
    /* Necessary so that a tab can be shifted down to overlay the border of the box below. */
    overflow-x: visible;
    overflow-y: visible;
}

 .jupyter-widgets.widget-tab > .p-TabBar > .p-TabBar-content {
    /* Make sure that the tab grows from bottom up */
    -webkit-box-align: end;
        -ms-flex-align: end;
            align-items: flex-end;
    min-width: 0;
    min-height: 0;
}

 .jupyter-widgets.widget-tab > .widget-tab-contents {
    width: 100%;
    -webkit-box-sizing: border-box;
            box-sizing: border-box;
    margin: 0;
    background: white;
    color: rgba(0, 0, 0, .8);
    border: 1px solid #9E9E9E;
    padding: 15px;
    -webkit-box-flex: 1;
        -ms-flex-positive: 1;
            flex-grow: 1;
    overflow: auto;
}

 .jupyter-widgets.widget-tab > .p-TabBar {
    font: 13px Helvetica, Arial, sans-serif;
    min-height: 25px;
}

 .jupyter-widgets.widget-tab > .p-TabBar .p-TabBar-tab {
    -webkit-box-flex: 0;
        -ms-flex: 0 1 144px;
            flex: 0 1 144px;
    min-width: 35px;
    min-height: 25px;
    line-height: 24px;
    margin-left: -1px;
    padding: 0px 10px;
    background: #EEEEEE;
    color: rgba(0, 0, 0, .5);
    border: 1px solid #9E9E9E;
    border-bottom: none;
    position: relative;
}

 .jupyter-widgets.widget-tab > .p-TabBar .p-TabBar-tab.p-mod-current {
    color: rgba(0, 0, 0, 1.0);
    /* We want the background to match the tab content background */
    background: white;
    min-height: 26px;
    -webkit-transform: translateY(1px);
            transform: translateY(1px);
    overflow: visible;
}

 .jupyter-widgets.widget-tab > .p-TabBar .p-TabBar-tab.p-mod-current:before {
    position: absolute;
    top: -1px;
    left: -1px;
    content: '';
    height: 2px;
    width: calc(100% + 2px);
    background: #2196F3;
}

 .jupyter-widgets.widget-tab > .p-TabBar .p-TabBar-tab:first-child {
    margin-left: 0;
}

 .jupyter-widgets.widget-tab > .p-TabBar .p-TabBar-tab:hover:not(.p-mod-current) {
    background: white;
    color: rgba(0, 0, 0, .8);
}

 .jupyter-widgets.widget-tab > .p-TabBar .p-mod-closable > .p-TabBar-tabCloseIcon {
    margin-left: 4px;
}

 .jupyter-widgets.widget-tab > .p-TabBar .p-mod-closable > .p-TabBar-tabCloseIcon:before {
    font-family: FontAwesome;
    content: '\F00D'; /* close */
}

 .jupyter-widgets.widget-tab > .p-TabBar .p-TabBar-tabIcon,
.jupyter-widgets.widget-tab > .p-TabBar .p-TabBar-tabLabel,
.jupyter-widgets.widget-tab > .p-TabBar .p-TabBar-tabCloseIcon {
    line-height: 24px;
}

 /* Accordion Widget */

 .p-Collapse {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-orient: vertical;
    -webkit-box-direction: normal;
        -ms-flex-direction: column;
            flex-direction: column;
    -webkit-box-align: stretch;
        -ms-flex-align: stretch;
            align-items: stretch;
}

 .p-Collapse-header {
    padding: 4px;
    cursor: pointer;
    color: rgba(0, 0, 0, .5);
    background-color: #EEEEEE;
    border: 1px solid #9E9E9E;
    padding: 10px 15px;
    font-weight: bold;
}

 .p-Collapse-header:hover {
    background-color: white;
    color: rgba(0, 0, 0, .8);
}

 .p-Collapse-open > .p-Collapse-header {
    background-color: white;
    color: rgba(0, 0, 0, 1.0);
    cursor: default;
    border-bottom: none;
}

 .p-Collapse .p-Collapse-header::before {
    content: '\F0DA\A0';  /* caret-right, non-breaking space */
    display: inline-block;
    font: normal normal normal 14px/1 FontAwesome;
    font-size: inherit;
    text-rendering: auto;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}

 .p-Collapse-open > .p-Collapse-header::before {
    content: '\F0D7\A0'; /* caret-down, non-breaking space */
}

 .p-Collapse-contents {
    padding: 15px;
    background-color: white;
    color: rgba(0, 0, 0, .8);
    border-left: 1px solid #9E9E9E;
    border-right: 1px solid #9E9E9E;
    border-bottom: 1px solid #9E9E9E;
    overflow: auto;
}

 .p-Accordion {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-orient: vertical;
    -webkit-box-direction: normal;
        -ms-flex-direction: column;
            flex-direction: column;
    -webkit-box-align: stretch;
        -ms-flex-align: stretch;
            align-items: stretch;
}

 .p-Accordion .p-Collapse {
    margin-bottom: 0;
}

 .p-Accordion .p-Collapse + .p-Collapse {
    margin-top: 4px;
}

 /* HTML widget */

 .widget-html, .widget-htmlmath {
    font-size: 13px;
}

 .widget-html > .widget-html-content, .widget-htmlmath > .widget-html-content {
    /* Fill out the area in the HTML widget */
    -ms-flex-item-align: stretch;
        align-self: stretch;
    -webkit-box-flex: 1;
        -ms-flex-positive: 1;
            flex-grow: 1;
    -ms-flex-negative: 1;
        flex-shrink: 1;
    /* Makes sure the baseline is still aligned with other elements */
    line-height: 28px;
    /* Make it possible to have absolutely-positioned elements in the html */
    position: relative;
}
</style><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/varInspector/jquery.tablesorter.min" src="./README_files/jquery.tablesorter.min.js.download"></script><style type="text/css">@font-face {font-family: STIXMathJax_Main-italic; src: url('http://localhost:8888/static/components/MathJax/fonts/HTML-CSS/STIX-Web/woff/STIXMathJax_Main-Italic.woff?V=2.7.4') format('woff'), url('http://localhost:8888/static/components/MathJax/fonts/HTML-CSS/STIX-Web/otf/STIXMathJax_Main-Italic.otf?V=2.7.4') format('opentype')}
</style><style type="text/css">@font-face {font-family: STIXMathJax_Main; src: url('http://localhost:8888/static/components/MathJax/fonts/HTML-CSS/STIX-Web/woff/STIXMathJax_Main-Regular.woff?V=2.7.4') format('woff'), url('http://localhost:8888/static/components/MathJax/fonts/HTML-CSS/STIX-Web/otf/STIXMathJax_Main-Regular.otf?V=2.7.4') format('opentype')}
</style><link id="favicon" type="image/x-icon" rel="shortcut icon" href="http://localhost:8888/static/base/images/favicon-notebook.ico"></head>

<body class="notebook_app command_mode" data-jupyter-api-token="52c38a14dd2558403e4ca62e1a12ae0445fb373538fc29b9" data-base-url="/" data-ws-url="" data-notebook-name="Recommander_Systems_Project.ipynb" data-notebook-path="Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb" dir="ltr" style=""><div style="visibility: hidden; overflow: hidden; position: absolute; top: 0px; height: 1px; width: auto; padding: 0px; border: 0px; margin: 0px; text-align: left; text-indent: 0px; text-transform: none; line-height: normal; letter-spacing: normal; word-spacing: normal;"><div id="MathJax_Hidden"><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br></div></div><div id="MathJax_Message" style="display: none;"></div>

<noscript>
    <div id='noscript'>
      Jupyter Notebook requires JavaScript.<br>
      Please enable it to proceed. 
  </div>
</noscript>

<div id="header" style="display: block;">
  <div id="header-container" class="container">
  <div id="ipython_notebook" class="nav navbar-brand"><a href="http://localhost:8888/tree?token=52c38a14dd2558403e4ca62e1a12ae0445fb373538fc29b9" title="dashboard">
      <img src="./README_files/logo.png" alt="Jupyter Notebook">
  </a></div>

  


<span id="save_widget" class="save_widget">
    <span id="notebook_name" class="filename">Recommander_Systems_Project</span>
    <span class="checkpoint_status" title="lun. 4 mars 2019 09:40">Last Checkpoint: Hier à 09:40</span>
    <span class="autosave_status">(autosaved)</span>
<i id="notebook-trusted-indicator" class="fa notebook-trusted fa-check" title="Notebook is trusted"></i></span>

<span id="kernel_logo_widget">
  
  <img class="current_kernel_logo" alt="Current Kernel Logo" src="./README_files/logo-64x64.png" title="Python 3" style="display: inline;">
  
</span>


  
  
  
  

    <span id="login_widget">
      
        <button id="logout" class="btn btn-sm navbar-btn">Logout</button>
      
    </span>

  

  
  
  </div>
  <div class="header-bar"></div>

  
<div id="menubar-container" class="container">
<div id="menubar">
    <div id="menus" class="navbar navbar-default" role="navigation">
        <div class="container-fluid">
            <button type="button" class="btn btn-default navbar-btn navbar-toggle" data-toggle="collapse" data-target=".navbar-collapse">
              <i class="fa fa-bars"></i>
              <span class="navbar-text">Menu</span>
            </button>
            <p id="kernel_indicator" class="navbar-text indicator_area">
              <span class="kernel_indicator_name">Python 3</span>
              <i id="kernel_indicator_icon" class="kernel_idle_icon" title="Kernel Idle"></i>
            </p>
            <i id="readonly-indicator" class="navbar-text" title="This notebook is read-only" style="display: none;">
                <span class="fa-stack">
                    <i class="fa fa-save fa-stack-1x"></i>
                    <i class="fa fa-ban fa-stack-2x text-danger"></i>
                </span>
            </i>
            <i id="modal_indicator" class="navbar-text modal_indicator" title="Command Mode"></i>
            <span id="notification_area"><div id="notification_kernel" class="notification_widget btn btn-xs navbar-btn undefined info" style="display: none;"><span></span></div><div id="notification_notebook" class="notification_widget btn btn-xs navbar-btn" style="display: none;"><span></span></div><div id="notification_trusted" class="notification_widget btn btn-xs navbar-btn" style="cursor: help;" disabled="disabled"><span title="Javascript enabled for notebook display">Trusted</span></div><div id="notification_widgets" class="notification_widget btn btn-xs navbar-btn" style="display: none;"><span></span></div></span>
            <div class="navbar-collapse collapse">
              <ul class="nav navbar-nav">
                <li class="dropdown"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#" class="dropdown-toggle" data-toggle="dropdown">File</a>
                    <ul id="file_menu" class="dropdown-menu">
                        <li id="new_notebook" class="dropdown-submenu">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">New Notebook</a>
                            <ul class="dropdown-menu" id="menu-new-notebook-submenu"><li id="new-notebook-submenu-python3"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Python 3</a></li></ul>
                        </li>
                        <li id="open_notebook" title="Opens a new window with the Dashboard view">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Open...</a></li>
                        <!-- <hr/> -->
                        <li class="divider"></li>
                        <li id="copy_notebook" title="Open a copy of this notebook&#39;s contents and start a new kernel">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Make a Copy...</a></li>
                        <li id="save_notebook_as" title="Save a copy of the notebook&#39;s contents and start a new kernel">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Save as...</a></li>
                        <li id="rename_notebook"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Rename...</a></li>
                        <li id="save_checkpoint"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Save and Checkpoint</a></li>
                        <!-- <hr/> -->
                        <li class="divider"></li>
                        <li id="restore_checkpoint" class="dropdown-submenu"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Revert to Checkpoint</a>
                          <ul class="dropdown-menu"><li><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">lundi 4 mars 2019 09:40</a></li></ul>
                        </li>
                        <li class="divider"></li>
                        <li id="print_preview"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Print Preview</a></li>
                        <li class="dropdown-submenu"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Download as</a>
                            <ul id="download_menu" class="dropdown-menu">
                                <li id="download_ipynb"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Notebook (.ipynb)</a></li>
                                <li id="download_script"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Python (.py)</a></li>
                                <li id="download_html"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">HTML (.html)</a></li>
                                <li id="download_slides"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Reveal.js slides (.html)</a></li>
                                <li id="download_markdown"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Markdown (.md)</a></li>
                                <li id="download_rst"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">reST (.rst)</a></li>
                                <li id="download_latex"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">LaTeX (.tex)</a></li>
                                <li id="download_pdf"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">PDF via LaTeX (.pdf)</a></li>
                                
                                <li id="download_asciidoc">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">asciidoc (.asciidoc)</a>
                                </li>
                                
                                <li id="download_custom">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">custom (.txt)</a>
                                </li>
                                
                                <li id="download_html">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">custom (.html)</a>
                                </li>
                                
                                <li id="download_html_ch">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">custom (.html)</a>
                                </li>
                                
                                <li id="download_html_embed">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">custom (.html)</a>
                                </li>
                                
                                <li id="download_html_toc">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">custom (.html)</a>
                                </li>
                                
                                <li id="download_html_with_lenvs">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">custom (.html)</a>
                                </li>
                                
                                <li id="download_html_with_toclenvs">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">custom (.html)</a>
                                </li>
                                
                                <li id="download_latex">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">latex (.tex)</a>
                                </li>
                                
                                <li id="download_latex_with_lenvs">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">latex (.tex)</a>
                                </li>
                                
                                <li id="download_markdown">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">markdown (.md)</a>
                                </li>
                                
                                <li id="download_notebook">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">notebook (.ipynb)</a>
                                </li>
                                
                                <li id="download_pdf">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">pdf (.tex)</a>
                                </li>
                                
                                <li id="download_python">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">python (.py)</a>
                                </li>
                                
                                <li id="download_rst">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">rst (.rst)</a>
                                </li>
                                
                                <li id="download_script">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">custom (.txt)</a>
                                </li>
                                
                                <li id="download_selectLanguage">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">notebook (.ipynb)</a>
                                </li>
                                
                                <li id="download_slides">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">slides (.slides.html)</a>
                                </li>
                                
                                <li id="download_slides_with_lenvs">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">slides (.slides.html)</a>
                                </li>
                                
                            <li id="download_html_embed"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">HTML Embedded (.html)</a></li></ul>
                        </li>
                        <li class="dropdown-submenu hidden"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Deploy as</a>
                            <ul id="deploy_menu" class="dropdown-menu"></ul>
                        </li>
                        <li class="divider"></li>
                        <li id="trust_notebook" title="Trust the output of this notebook" class="disabled">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Trusted Notebook</a></li>
                        <li class="divider"></li>
                        <li id="close_and_halt" title="Shutdown this notebook&#39;s kernel, and close this window">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Close and Halt</a></li>
                    </ul>
                </li>
                <li class="dropdown"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#" class="dropdown-toggle" data-toggle="dropdown">Edit</a>
                    <ul id="edit_menu" class="dropdown-menu">
                        <li id="cut_cell"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Cut Cells</a></li>
                        <li id="copy_cell"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Copy Cells</a></li>
                        <li id="paste_cell_above" class=""><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Paste Cells Above</a></li>
                        <li id="paste_cell_below" class=""><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Paste Cells Below</a></li>
                        <li id="paste_cell_replace" class=""><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Paste Cells &amp; Replace</a></li>
                        <li id="delete_cell"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Delete Cells</a></li>
                        <li id="undelete_cell" class=""><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Undo Delete Cells</a></li>
                        <li class="divider"></li>
                        <li id="split_cell"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Split Cell</a></li>
                        <li id="merge_cell_above"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Merge Cell Above</a></li>
                        <li id="merge_cell_below"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Merge Cell Below</a></li>
                        <li class="divider"></li>
                        <li id="move_cell_up"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Move Cell Up</a></li>
                        <li id="move_cell_down"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Move Cell Down</a></li>
                        <li class="divider"></li>
                        <li id="edit_nb_metadata"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Edit Notebook Metadata</a></li>
                        <li class="divider"></li>
                        <li id="find_and_replace"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#"> Find and Replace </a></li>
                        <li class="divider"></li>
                        <li id="cut_cell_attachments"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Cut Cell Attachments</a></li>
                        <li id="copy_cell_attachments"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Copy Cell Attachments</a></li>
                        <li id="paste_cell_attachments" class="disabled"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Paste Cell Attachments</a></li>
                        <li class="divider"></li>
                        <li id="insert_image" class="disabled"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#"> Insert Image </a></li>
                    <li class="divider"></li><li><a target="_blank" title="Opens in a new window" href="http://localhost:8888/nbextensions/"> <i class="fa fa-cogs menu-icon pull-right"></i><span>nbextensions config</span></a></li></ul>
                </li>
                <li class="dropdown"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#" class="dropdown-toggle" data-toggle="dropdown" aria-expanded="false">View</a>
                    <ul id="view_menu" class="dropdown-menu">
                        <li id="toggle_header" title="Show/Hide the logo and notebook title (above menu bar)">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Toggle Header</a>
                        </li>
                        <li id="toggle_toolbar" title="Show/Hide the action icons (below menu bar)">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Toggle Toolbar</a>
                        </li>
                        <li id="toggle_line_numbers" title="Show/Hide line numbers in cells">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Toggle Line Numbers</a>
                        </li>
                        <li id="menu-cell-toolbar" class="dropdown-submenu">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Cell Toolbar</a>
                            <ul class="dropdown-menu" id="menu-cell-toolbar-submenu"><li data-name="None"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">None</a></li><li data-name="Edit%20Metadata"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Edit Metadata</a></li><li data-name="Raw%20Cell%20Format"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Raw Cell Format</a></li><li data-name="Slideshow"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Slideshow</a></li><li data-name="Attachments"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Attachments</a></li><li data-name="Tags"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Tags</a></li></ul>
                        </li>
                    </ul>
                </li>
                <li class="dropdown"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#" class="dropdown-toggle" data-toggle="dropdown">Insert</a>
                    <ul id="insert_menu" class="dropdown-menu">
                        <li id="insert_cell_above" title="Insert an empty Code cell above the currently active cell">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Insert Cell Above</a></li>
                        <li id="insert_cell_below" title="Insert an empty Code cell below the currently active cell">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Insert Cell Below</a></li>
                    <li class="divider"></li><li><a title="Insert a heading cell above the selected cell" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Insert Heading Above</a></li><li><a title="Insert a heading cell below the selected cell&#39;s section" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Insert Heading Below</a></li></ul>
                </li>
                <li class="dropdown"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#" class="dropdown-toggle" data-toggle="dropdown">Cell</a>
                    <ul id="cell_menu" class="dropdown-menu">
                        <li id="run_cell" title="Run this cell, and move cursor to the next one">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Run Cells</a></li>
                        <li id="run_cell_select_below" title="Run this cell, select below">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Run Cells and Select Below</a></li>
                        <li id="run_cell_insert_below" title="Run this cell, insert below">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Run Cells and Insert Below</a></li>
                        <li id="run_all_cells" title="Run all cells in the notebook">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Run All</a></li>
                        <li id="run_all_cells_above" title="Run all cells above (but not including) this cell">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Run All Above</a></li>
                        <li id="run_all_cells_below" title="Run this cell and all cells below it">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Run All Below</a></li>
                        <li class="divider"></li>
                        <li id="change_cell_type" class="dropdown-submenu" title="All cells in the notebook have a cell type. By default, new cells are created as &#39;Code&#39; cells">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Cell Type</a>
                            <ul class="dropdown-menu">
                              <li id="to_code" title="Contents will be sent to the kernel for execution, and output will display in the footer of cell">
                                  <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Code</a></li>
                              <li id="to_markdown" title="Contents will be rendered as HTML and serve as explanatory text">
                                  <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Markdown</a></li>
                              <li id="to_raw" title="Contents will pass through nbconvert unmodified">
                                  <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Raw NBConvert</a></li>
                            </ul>
                        </li>
                        <li class="divider"></li>
                        <li id="current_outputs" class="dropdown-submenu"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Current Outputs</a>
                            <ul class="dropdown-menu">
                                <li id="toggle_current_output" title="Hide/Show the output of the current cell">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Toggle</a>
                                </li>
                                <li id="toggle_current_output_scroll" title="Scroll the output of the current cell">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Toggle Scrolling</a>
                                </li>
                                <li id="clear_current_output" title="Clear the output of the current cell">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Clear</a>
                                </li>
                            </ul>
                        </li>
                        <li id="all_outputs" class="dropdown-submenu"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">All Output</a>
                            <ul class="dropdown-menu">
                                <li id="toggle_all_output" title="Hide/Show the output of all cells">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Toggle</a>
                                </li>
                                <li id="toggle_all_output_scroll" title="Scroll the output of all cells">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Toggle Scrolling</a>
                                </li>
                                <li id="clear_all_output" title="Clear the output of all cells">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Clear</a>
                                </li>
                            </ul>
                        </li>
                    </ul>
                </li>
                <li class="dropdown"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#" class="dropdown-toggle" data-toggle="dropdown" aria-expanded="false">Kernel</a>
                    <ul id="kernel_menu" class="dropdown-menu">
                        <li id="int_kernel" title="Send Keyboard Interrupt (CTRL-C) to the Kernel">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Interrupt</a>
                        </li>
                        <li id="restart_kernel" title="Restart the Kernel">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Restart</a>
                        </li>
                        <li id="restart_clear_output" title="Restart the Kernel and clear all output">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Restart &amp; Clear Output</a>
                        </li>
                        <li id="restart_run_all" title="Restart the Kernel and re-run the notebook">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Restart &amp; Run All</a>
                        </li>
                        <li id="reconnect_kernel" title="Reconnect to the Kernel">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Reconnect</a>
                        </li>
                        <li id="shutdown_kernel" title="Shutdown the Kernel">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Shutdown</a>
                        </li>
                        <li class="divider"></li>
                        <li id="menu-change-kernel" class="dropdown-submenu">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Change kernel</a>
                            <ul class="dropdown-menu" id="menu-change-kernel-submenu"><li id="kernel-submenu-python3"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Python 3</a></li></ul>
                        </li>
                    </ul>
                </li><li id="Navigate" class="dropdown"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#" id="Navigate_sub" class="dropdown-toggle" data-toggle="dropdown">Navigate</a><ul id="Navigate_menu" class="dropdown-menu ui-resizable" style=""><div id="navigate_menu" class="toc" style="width: 160px; height: 0px;"><ul class="toc-item"><li><span><i class="fa fa-fw fa-caret-down"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Recommender-System-with-Python" data-toc-modified-id="Recommender-System-with-Python-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>Recommender System with Python</a></span><ul class="toc-item"><li><span><i class="fa fa-fw"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Overview" data-toc-modified-id="Overview-1.1"><span class="toc-item-num">1.1&nbsp;&nbsp;</span>Overview</a></span></li><li><span><i class="fa fa-fw"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Exploratory-Data-Analysis" data-toc-modified-id="Exploratory-Data-Analysis-1.2"><span class="toc-item-num">1.2&nbsp;&nbsp;</span>Exploratory Data Analysis</a></span></li><li><span><i class="fa fa-fw"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Recommender-System-for-similar-movie" data-toc-modified-id="Recommender-System-for-similar-movie-1.3" class="toc-item-highlight-select"><span class="toc-item-num">1.3&nbsp;&nbsp;</span>Recommender System for similar movie</a></span></li></ul></li></ul></div><div class="ui-resizable-handle ui-resizable-e" style="z-index: 90;"></div><div class="ui-resizable-handle ui-resizable-s" style="z-index: 90;"></div><div class="ui-resizable-handle ui-resizable-se ui-icon ui-icon-gripsmall-diagonal-se" style="z-index: 90;"></div></ul></li>
                <li class="dropdown"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#" data-toggle="dropdown" class="dropdown-toggle">Widgets</a><ul id="widget-submenu" class="dropdown-menu"><li title="Save the notebook with the widget state information for static rendering"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Save Notebook Widget State</a></li><li title="Clear the widget state information from the notebook"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Clear Notebook Widget State</a></li><ul class="divider"></ul><li title="Download the widget state as a JSON file"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Download Widget State</a></li><li title="Embed interactive widgets"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Embed Widgets</a></li></ul></li><li class="dropdown"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#" class="dropdown-toggle" data-toggle="dropdown">Help</a>
                    <ul id="help_menu" class="dropdown-menu">
                        
                        <li id="notebook_tour" title="A quick tour of the notebook user interface"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">User Interface Tour</a></li>
                        <li id="keyboard_shortcuts" title="Opens a tooltip with all keyboard shortcuts"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Keyboard Shortcuts</a></li>
                        <li id="edit_keyboard_shortcuts" title="Opens a dialog allowing you to edit Keyboard shortcuts"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">Edit Keyboard Shortcuts</a></li>
                        <li class="divider"></li>
                        

						
                        
                            
                                <li><a rel="noreferrer" href="http://nbviewer.jupyter.org/github/ipython/ipython/blob/3.x/examples/Notebook/Index.ipynb" target="_blank" title="Opens in a new window">
                                
                                    <i class="fa fa-external-link menu-icon pull-right"></i>
                                

                                Notebook Help
                                </a></li>
                            
                                <li><a rel="noreferrer" href="https://help.github.com/articles/markdown-basics/" target="_blank" title="Opens in a new window">
                                
                                    <i class="fa fa-external-link menu-icon pull-right"></i>
                                

                                Markdown
                                </a></li>
                            
                            
                        
                        <li><a title="Jupyter_contrib_nbextensions documentation" id="jupyter_contrib_nbextensions_help" href="http://jupyter-contrib-nbextensions.readthedocs.io/en/latest/" target="_blank">Jupyter-contrib <br> nbextensions<i class="fa fa-external-link menu-icon pull-right"></i></a></li><li id="kernel-help-links" class="divider"></li><li><a target="_blank" title="Opens in a new window" href="https://docs.python.org/3.7?v=20190305083854"><i class="fa fa-external-link menu-icon pull-right"></i><span>Python Reference</span></a></li><li><a target="_blank" title="Opens in a new window" href="https://ipython.org/documentation.html?v=20190305083854"><i class="fa fa-external-link menu-icon pull-right"></i><span>IPython Reference</span></a></li><li><a target="_blank" title="Opens in a new window" href="https://docs.scipy.org/doc/numpy/reference/?v=20190305083854"><i class="fa fa-external-link menu-icon pull-right"></i><span>NumPy Reference</span></a></li><li><a target="_blank" title="Opens in a new window" href="https://docs.scipy.org/doc/scipy/reference/?v=20190305083854"><i class="fa fa-external-link menu-icon pull-right"></i><span>SciPy Reference</span></a></li><li><a target="_blank" title="Opens in a new window" href="https://matplotlib.org/contents.html?v=20190305083854"><i class="fa fa-external-link menu-icon pull-right"></i><span>Matplotlib Reference</span></a></li><li><a target="_blank" title="Opens in a new window" href="http://docs.sympy.org/latest/index.html?v=20190305083854"><i class="fa fa-external-link menu-icon pull-right"></i><span>SymPy Reference</span></a></li><li><a target="_blank" title="Opens in a new window" href="https://pandas.pydata.org/pandas-docs/stable/?v=20190305083854"><i class="fa fa-external-link menu-icon pull-right"></i><span>pandas Reference</span></a></li><li class="divider"></li>
                        <li title="About Jupyter Notebook"><a id="notebook_about" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#">About</a></li>
                        
                    </ul>
                </li>
              </ul>
            </div>
        </div>
    </div>
</div>

<div id="maintoolbar" class="navbar">
  <div class="toolbar-inner navbar-inner navbar-nobg">
    <div id="maintoolbar-container" class="container toolbar"><div class="btn-group" id="save-notbook"><button class="btn btn-default" title="Save and Checkpoint" data-jupyter-action="jupyter-notebook:save-notebook"><i class="fa-save fa"></i></button></div><div class="btn-group" id="insert_above_below"><button class="btn btn-default" title="insert cell below" data-jupyter-action="jupyter-notebook:insert-cell-below"><i class="fa-plus fa"></i></button></div><div class="btn-group" id="cut_copy_paste"><button class="btn btn-default" title="cut selected cells" data-jupyter-action="jupyter-notebook:cut-cell"><i class="fa-cut fa"></i></button><button class="btn btn-default" title="copy selected cells" data-jupyter-action="jupyter-notebook:copy-cell"><i class="fa-copy fa"></i></button><button class="btn btn-default" title="paste cells below" data-jupyter-action="jupyter-notebook:paste-cell-below"><i class="fa-paste fa"></i></button></div><div class="btn-group" id="move_up_down"><button class="btn btn-default" title="move selected cells up" data-jupyter-action="jupyter-notebook:move-cell-up"><i class="fa-arrow-up fa"></i></button><button class="btn btn-default" title="move selected cells down" data-jupyter-action="jupyter-notebook:move-cell-down"><i class="fa-arrow-down fa"></i></button></div><div class="btn-group" id="run_int"><button class="btn btn-default" title="Run" data-jupyter-action="jupyter-notebook:run-cell-and-select-next"><i class="fa-step-forward fa"></i><span class="toolbar-btn-label">Run</span></button><button class="btn btn-default" title="interrupt the kernel" data-jupyter-action="jupyter-notebook:interrupt-kernel"><i class="fa-stop fa"></i></button><button class="btn btn-default" title="restart the kernel (with dialog)" data-jupyter-action="jupyter-notebook:confirm-restart-kernel"><i class="fa-repeat fa"></i></button><button class="btn btn-default" title="restart the kernel, then re-run the whole notebook (with dialog)" data-jupyter-action="jupyter-notebook:confirm-restart-kernel-and-run-all-cells"><i class="fa-forward fa"></i></button></div><select id="cell_type" class="form-control select-xs"><option value="code">Code</option><option value="markdown">Markdown</option><option value="raw">Raw NBConvert</option><option value="heading">Heading</option><option value="multiselect" disabled="disabled" style="display: none;">-</option></select><div class="btn-group"><button class="btn btn-default" title="open the command palette" data-jupyter-action="jupyter-notebook:show-command-palette"><i class="fa-keyboard-o fa"></i></button></div><div class="btn-group"><button class="btn btn-default" title="Variable Inspector" data-jupyter-action="varInspector:toggle-variable-inspector" id="varInspector_button"><i class="fa-crosshairs fa"></i></button></div><div class="btn-group"><button class="btn btn-default" title="Increase code font size" data-jupyter-action="code_font_size:increase-code-font-size"><i class="fa-search-plus fa"></i></button><button class="btn btn-default" title="Decrease code font size" data-jupyter-action="code_font_size:decrease-code-font-size"><i class="fa-search-minus fa"></i></button></div><div class="btn-group"><button class="btn btn-default" title="Create/Edit Gist of Notebook" data-jupyter-action="gist_it:create-gist-from-notebook"><i class="fa-github fa"></i></button></div><div class="btn-group"><button class="btn btn-default" title="Table of Contents" data-jupyter-action="toc2:toggle-toc" id="toc_button"><i class="fa-list fa"></i></button></div><div class="btn-group" id="code_prettify_button"><button class="btn btn-default" title="code_prettify selected cell(s) (add shift for all cells)"><i class="fa-legal fa"></i></button></div><div class="btn-group" id="autopep8_button"><button class="btn btn-default" title="autopep8 selected cell(s) (add shift for all cells)"><i class="fa-legal fa"></i></button></div></div>
  </div>
</div>
</div>

<div class="lower-header-bar"></div>

</div>

<div id="site" style="display: block; height: 499px;"><div id="toc-wrapper" style="display: none; position: relative; width: 20%; top: 109.778px; left: 0px;" class="ui-draggable ui-resizable sidebar-wrapper"><div id="toc-header"><span class="header">Contents </span><i class="fa fa-fw hide-btn" title="Hide ToC"></i><i class="fa fa-fw fa-refresh" title="Reload ToC"></i><i class="fa fa-fw fa-cog" title="ToC settings"></i></div><div id="toc" class="toc"><ul class="toc-item"><li><span class="highlight_on_scroll"><i class="fa fa-fw fa-caret-down"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Recommender-System-with-Python" data-toc-modified-id="Recommender-System-with-Python-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>Recommender System with Python</a></span><ul class="toc-item"><li><span class=""><i class="fa fa-fw"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Overview" data-toc-modified-id="Overview-1.1"><span class="toc-item-num">1.1&nbsp;&nbsp;</span>Overview</a></span></li><li><span class=""><i class="fa fa-fw"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Exploratory-Data-Analysis" data-toc-modified-id="Exploratory-Data-Analysis-1.2"><span class="toc-item-num">1.2&nbsp;&nbsp;</span>Exploratory Data Analysis</a></span></li><li><span class=""><i class="fa fa-fw"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Recommender-System-for-similar-movie" data-toc-modified-id="Recommender-System-for-similar-movie-1.3" class="toc-item-highlight-select"><span class="toc-item-num">1.3&nbsp;&nbsp;</span>Recommender System for similar movie</a></span></li></ul></li></ul></div><div class="ui-resizable-handle ui-resizable-n" style="z-index: 90;"></div><div class="ui-resizable-handle ui-resizable-e ui-icon ui-icon-grip-dotted-vertical" style="z-index: 90;"></div><div class="ui-resizable-handle ui-resizable-s" style="z-index: 90;"></div><div class="ui-resizable-handle ui-resizable-w" style="z-index: 90;"></div><div class="ui-resizable-handle ui-resizable-se ui-icon-gripsmall-diagonal-se" style="z-index: 90;"></div><div class="ui-resizable-handle ui-resizable-sw" style="z-index: 90;"></div><div class="ui-resizable-handle ui-resizable-ne" style="z-index: 90;"></div><div class="ui-resizable-handle ui-resizable-nw" style="z-index: 90;"></div></div>


<div id="ipython-main-app">
    <div id="notebook_panel">
        <div id="notebook" tabindex="-1"><div class="container" id="notebook-container"><div class="cell text_cell rendered collapsible_headings_ellipsis unselected" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h1"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59721px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 33px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 21.3333px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-1"># Recommender System with Python</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 33px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 45px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h1 id="Recommender-System-with-Python" data-toc-modified-id="Recommender-System-with-Python-1"><a class="toc-mod-link" id="Recommender-System-with-Python-1"></a><span class="toc-item-num">1&nbsp;&nbsp;</span>Recommender System with Python<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Recommender-System-with-Python">¶</a></h1>
</div></div></div><div class="cell text_cell unselected rendered collapsible_headings_ellipsis" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h2"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59721px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 32px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 20.4444px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-2">## Overview</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 32px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 44px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h2 id="Overview" data-toc-modified-id="Overview-1.1"><a class="toc-mod-link" id="Overview-1.1"></a><span class="toc-item-num">1.1&nbsp;&nbsp;</span>Overview<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Overview">¶</a></h2>
</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59723px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 45px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.4444px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">we will be working with movielens dataset. The dataset consist of two .csv files, movies.csv and ratings.csv. If you want, you can directly downloaded these files from the provided link.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 57px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>we will be working with movielens dataset. The dataset consist of two .csv files, movies.csv and ratings.csv. If you want, you can directly downloaded these files from the provided link.</p>
</div></div></div><div class="cell text_cell unselected rendered collapsible_headings_ellipsis" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h5"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59723px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 29px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 17.7778px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-5">##### Let's import some libraries</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 29px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 41px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h5 id="Let&#39;s-import-some-libraries">Let's import some libraries<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Let&#39;s-import-some-libraries">¶</a></h5>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[1]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59961px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 154.819px; margin-bottom: -16px; border-right-width: 14px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><span><span>​</span>x</span></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-keyword">import</span> <span class="cm-variable">numpy</span> <span class="cm-keyword">as</span> <span class="cm-variable">np</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-keyword">import</span> <span class="cm-variable">pandas</span> <span class="cm-keyword">as</span> <span class="cm-variable">pd</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="height: 59px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered collapsible_headings_ellipsis" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h5"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59723px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 29px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 17.7778px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-5">##### Let's read the datafiles</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 29px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 41px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h5 id="Let&#39;s-read-the-datafiles">Let's read the datafiles<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Let&#39;s-read-the-datafiles">¶</a></h5>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[2]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59961px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 270.264px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">movies</span> <span class="cm-operator">=</span> <span class="cm-variable">pd</span>.<span class="cm-property">read_csv</span>(<span class="cm-string">'movies.csv'</span>)</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 42px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[3]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59961px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 293.347px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">ratings</span>  <span class="cm-operator">=</span> <span class="cm-variable">pd</span>.<span class="cm-property">read_csv</span>(<span class="cm-string">'ratings.csv'</span>)</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 42px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered collapsible_headings_ellipsis" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h5"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59723px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 29px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 17.7778px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-5">##### Let's check the head of movies and ratings</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 29px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 41px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h5 id="Let&#39;s-check-the-head-of-movies-and-ratings">Let's check the head of movies and ratings<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Let&#39;s-check-the-head-of-movies-and-ratings">¶</a></h5>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[4]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.60059px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 108.639px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">movies</span>.<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 42px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[4]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movieId</th>
      <th>title</th>
      <th>genres</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Toy Story (1995)</td>
      <td>Adventure|Animation|Children|Comedy|Fantasy</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Jumanji (1995)</td>
      <td>Adventure|Children|Fantasy</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Grumpier Old Men (1995)</td>
      <td>Comedy|Romance</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Waiting to Exhale (1995)</td>
      <td>Comedy|Drama|Romance</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Father of the Bride Part II (1995)</td>
      <td>Comedy</td>
    </tr>
  </tbody>
</table>
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[5]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 116.333px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">ratings</span>.<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 42px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[5]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>userId</th>
      <th>movieId</th>
      <th>rating</th>
      <th>timestamp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>31</td>
      <td>2.5</td>
      <td>1260759144</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1029</td>
      <td>3.0</td>
      <td>1260759179</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>1061</td>
      <td>3.0</td>
      <td>1260759182</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>1129</td>
      <td>2.0</td>
      <td>1260759185</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>1172</td>
      <td>4.0</td>
      <td>1260759205</td>
    </tr>
  </tbody>
</table>
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59729px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 45px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.4444px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">In the ratings dataset, we have userId, movieId, rating that the movie got from a specific user, and the timestamp at which the movie got rating from the user. </span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 57px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>In the ratings dataset, we have userId, movieId, rating that the movie got from a specific user, and the timestamp at which the movie got rating from the user. </p>
</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59729px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 45px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.4445px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">If we look at both ratings and movies datasets, movieId column is a common column. Let's merge the dataframes on movieId and output the head() of the merged data.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 57px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>If we look at both ratings and movies datasets, movieId column is a common column. Let's merge the dataframes on movieId and output the head() of the merged data.</p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[6]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 354.903px; margin-bottom: -16px; border-right-width: 14px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">df</span> <span class="cm-operator">=</span> <span class="cm-variable">pd</span>.<span class="cm-property">merge</span>(<span class="cm-variable">ratings</span>,<span class="cm-variable">movies</span>, <span class="cm-variable">on</span> <span class="cm-operator">=</span> <span class="cm-string">'movieId'</span>)</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">df</span>.<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="height: 59px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[6]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>userId</th>
      <th>movieId</th>
      <th>rating</th>
      <th>timestamp</th>
      <th>title</th>
      <th>genres</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>31</td>
      <td>2.5</td>
      <td>1260759144</td>
      <td>Dangerous Minds (1995)</td>
      <td>Drama</td>
    </tr>
    <tr>
      <th>1</th>
      <td>7</td>
      <td>31</td>
      <td>3.0</td>
      <td>851868750</td>
      <td>Dangerous Minds (1995)</td>
      <td>Drama</td>
    </tr>
    <tr>
      <th>2</th>
      <td>31</td>
      <td>31</td>
      <td>4.0</td>
      <td>1273541953</td>
      <td>Dangerous Minds (1995)</td>
      <td>Drama</td>
    </tr>
    <tr>
      <th>3</th>
      <td>32</td>
      <td>31</td>
      <td>4.0</td>
      <td>834828440</td>
      <td>Dangerous Minds (1995)</td>
      <td>Drama</td>
    </tr>
    <tr>
      <th>4</th>
      <td>36</td>
      <td>31</td>
      <td>3.0</td>
      <td>847057202</td>
      <td>Dangerous Minds (1995)</td>
      <td>Drama</td>
    </tr>
  </tbody>
</table>
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered collapsible_headings_ellipsis" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h5"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 29px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 17.7778px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-5">##### Let's do some pre-processing on data</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 29px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 41px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h5 id="Let&#39;s-do-some-pre-processing-on-data">Let's do some pre-processing on data<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Let&#39;s-do-some-pre-processing-on-data">¶</a></h5>
</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59729px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 62px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>2</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.4444px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">The first thing we can do is to create a dataframe that tells us the average rating for the movie and number of ratings the movie we got.</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">To do this, we can use the groupby method.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 62px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 74px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>The first thing we can do is to create a dataframe that tells us the average rating for the movie and number of ratings the movie we got.
To do this, we can use the groupby method.</p>
</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59729px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 62px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.4445px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We need to groupby the movies on title and then grab the rating column to get its mean, so that we have the mean rating of each movie. We can also use sort_values(ascending = False) to re-arrange the entries from higher to lower mean rating and then check the head of dataframe, all in a single line code.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 62px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 74px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>We need to groupby the movies on title and then grab the rating column to get its mean, so that we have the mean rating of each movie. We can also use sort_values(ascending = False) to re-arrange the entries from higher to lower mean rating and then check the head of dataframe, all in a single line code.</p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[7]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 562.694px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">df</span>.<span class="cm-property">groupby</span>(<span class="cm-string">'title'</span>)[<span class="cm-string">'rating'</span>].<span class="cm-property">mean</span>().<span class="cm-property">sort_values</span>(<span class="cm-variable">ascending</span><span class="cm-operator">=</span><span class="cm-keyword">False</span>).<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 42px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[7]:</bdi></div><div class="output_subarea output_text output_result"><pre>title
Burn Up! (1991)                                     5.0
Absolute Giganten (1999)                            5.0
Gentlemen of Fortune (Dzhentlmeny udachi) (1972)    5.0
Erik the Viking (1989)                              5.0
Reality (2014)                                      5.0
Name: rating, dtype: float64</pre></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 28px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">There is an important situation to consider in the above groupby operation, while getting the mean rating.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 40px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>There is an important situation to consider in the above groupby operation, while getting the mean rating.</p>
</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59729px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 62px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>2</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">What if only 1 or 2 persons have watched a movie and gave a 5 stars rating to it.</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">On the other hand, there could be a movie that got a good number of ratings between 1 and 5 stars. The average in such situation will be less then 5 but the number of watcher are higher.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 62px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 74px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>What if only 1 or 2 persons have watched a movie and gave a 5 stars rating to it.
On the other hand, there could be a movie that got a good number of ratings between 1 and 5 stars. The average in such situation will be less then 5 but the number of watcher are higher.</p>
</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59729px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 62px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>2</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.4445px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Once again, groupby on title and grab the ratings column. Instead of mean, we want count for this task. We can again use sort_values(ascending =False) </span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">to order the entries and check the head of our dataset.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 62px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 74px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>Once again, groupby on title and grab the ratings column. Instead of mean, we want count for this task. We can again use sort_values(ascending =False) 
to order the entries and check the head of our dataset.</p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[8]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59961px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 570.111px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">df</span>.<span class="cm-property">groupby</span>(<span class="cm-string">'title'</span>)[<span class="cm-string">'rating'</span>].<span class="cm-property">count</span>().<span class="cm-property">sort_values</span>(<span class="cm-variable">ascending</span><span class="cm-operator">=</span><span class="cm-keyword">False</span>).<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 42px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[8]:</bdi></div><div class="output_subarea output_text output_result"><pre>title
Forrest Gump (1994)                          341
Pulp Fiction (1994)                          324
Shawshank Redemption, The (1994)             311
Silence of the Lambs, The (1991)             304
Star Wars: Episode IV - A New Hope (1977)    291
Name: rating, dtype: int64</pre></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 113px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>4</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">It looks like the top 5 famous movies don't have the 5 star average rating. </span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">This is fine, you can imagine, if the movie, e.g. Forrest Gump got 341 ratings, all ratings must be 5 star to get average value of 5. </span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Many of us may not know even the name of the movie with average 5 star rating, but, most of us might be familiar with the movies with most number of ratings, such as Start Wars in the list on number 5.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 113px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 125px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>It looks like the top 5 famous movies don't have the 5 star average rating. 
This is fine, you can imagine, if the movie, e.g. Forrest Gump got 341 ratings, all ratings must be 5 star to get average value of 5. </p>
<p>Many of us may not know even the name of the movie with average 5 star rating, but, most of us might be familiar with the movies with most number of ratings, such as Start Wars in the list on number 5.</p>
</div></div></div><div class="cell text_cell unselected rendered collapsible_headings_ellipsis" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h5"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 29px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 17.7778px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-5">##### Let's create a new dataframe rating, in which we group the movies with their mean or average rating. </span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 29px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 41px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h5 id="Let&#39;s-create-a-new-dataframe-rating,-in-which-we-group-the-movies-with-their-mean-or-average-rating.">Let's create a new dataframe rating, in which we group the movies with their mean or average rating.<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Let&#39;s-create-a-new-dataframe-rating,-in-which-we-group-the-movies-with-their-mean-or-average-rating.">¶</a></h5>
</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 28px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">we are going to use groupby on title and grab the rating columns to get its mean.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 40px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>we are going to use groupby on title and grab the rating columns to get its mean.</p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[9]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59961px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 462.556px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">rating</span> <span class="cm-operator">=</span> <span class="cm-variable">pd</span>.<span class="cm-property">DataFrame</span>(<span class="cm-variable">df</span>.<span class="cm-property">groupby</span>(<span class="cm-string">'title'</span>)[<span class="cm-string">'rating'</span>].<span class="cm-property">mean</span>())</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 42px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[10]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59961px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 108.639px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">rating</span>.<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 42px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[10]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>rating</th>
    </tr>
    <tr>
      <th>title</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>"Great Performances" Cats (1998)</th>
      <td>1.750000</td>
    </tr>
    <tr>
      <th>$9.99 (2008)</th>
      <td>3.833333</td>
    </tr>
    <tr>
      <th>'Hellboy': The Seeds of Creation (2004)</th>
      <td>2.000000</td>
    </tr>
    <tr>
      <th>'Neath the Arizona Skies (1934)</th>
      <td>0.500000</td>
    </tr>
    <tr>
      <th>'Round Midnight (1986)</th>
      <td>2.250000</td>
    </tr>
  </tbody>
</table>
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59741px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 45px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.4445px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">In the above dataframe, we got the average rating for each movie in rating column and name of the movie in title column. This does not make much sense for the movies who got several number of rating as compare to those who got very few.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 57px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>In the above dataframe, we got the average rating for each movie in rating column and name of the movie in title column. This does not make much sense for the movies who got several number of rating as compare to those who got very few.</p>
</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 28px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We need to look at the number of ratings as well. </span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 40px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>We need to look at the number of ratings as well. </p>
</div></div></div><div class="cell text_cell unselected rendered collapsible_headings_ellipsis" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h5"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 29px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 17.7778px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-5">##### Let's create another column n_ratings that tell us the number of ratings for each movie.</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 29px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 41px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h5 id="Let&#39;s-create-another-column-n_ratings-that-tell-us-the-number-of-ratings-for-each-movie.">Let's create another column n_ratings that tell us the number of ratings for each movie.<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Let&#39;s-create-another-column-n_ratings-that-tell-us-the-number-of-ratings-for-each-movie.">¶</a></h5>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[11]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 570.111px; margin-bottom: -16px; border-right-width: 14px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">rating</span>[<span class="cm-string">'n_ratings'</span>] <span class="cm-operator">=</span> <span class="cm-variable">pd</span>.<span class="cm-property">DataFrame</span>(<span class="cm-variable">df</span>.<span class="cm-property">groupby</span>(<span class="cm-string">'title'</span>)[<span class="cm-string">'rating'</span>].<span class="cm-property">count</span>())</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">rating</span>.<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="height: 59px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[11]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>rating</th>
      <th>n_ratings</th>
    </tr>
    <tr>
      <th>title</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>"Great Performances" Cats (1998)</th>
      <td>1.750000</td>
      <td>2</td>
    </tr>
    <tr>
      <th>$9.99 (2008)</th>
      <td>3.833333</td>
      <td>3</td>
    </tr>
    <tr>
      <th>'Hellboy': The Seeds of Creation (2004)</th>
      <td>2.000000</td>
      <td>1</td>
    </tr>
    <tr>
      <th>'Neath the Arizona Skies (1934)</th>
      <td>0.500000</td>
      <td>1</td>
    </tr>
    <tr>
      <th>'Round Midnight (1986)</th>
      <td>2.250000</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59741px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 28px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We have a dataframe rating with three columns title, rating which is actually average of mean rating, and n_rating.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 40px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>We have a dataframe rating with three columns title, rating which is actually average of mean rating, and n_rating.</p>
</div></div></div><div class="cell text_cell unselected rendered collapsible_headings_ellipsis" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h2"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 32px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 20.4444px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-2">## Exploratory Data Analysis</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 32px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 44px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h2 id="Exploratory-Data-Analysis" data-toc-modified-id="Exploratory-Data-Analysis-1.2"><a class="toc-mod-link" id="Exploratory-Data-Analysis-1.2"></a><span class="toc-item-num">1.2&nbsp;&nbsp;</span>Exploratory Data Analysis<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Exploratory-Data-Analysis">¶</a></h2>
</div></div></div><div class="cell text_cell unselected rendered collapsible_headings_ellipsis" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h5"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59741px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 29px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 17.7778px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-5">##### Let's import some librairies again</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 29px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 41px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h5 id="Let&#39;s-import-some-librairies-again">Let's import some librairies again<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Let&#39;s-import-some-librairies-again">¶</a></h5>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[12]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59985px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 247.181px; margin-bottom: -16px; border-right-width: 14px; min-height: 78px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-keyword">import</span> <span class="cm-variable">matplotlib</span>.<span class="cm-property">pyplot</span> <span class="cm-keyword">as</span> <span class="cm-variable">plt</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-keyword">import</span> <span class="cm-variable">seaborn</span> <span class="cm-keyword">as</span> <span class="cm-variable">sns</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">sns</span>.<span class="cm-property">set_style</span>(<span class="cm-string">'white'</span>)</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-operator">%</span><span class="cm-variable">matplotlib</span> <span class="cm-variable">inline</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 78px;"></div><div class="CodeMirror-gutters" style="height: 92px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59741px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 45px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.4445px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">To learn from our dataset, let's plot two histograms side-by-side, one for No. of ratings for movies, n_ratings column, and the other for average rating which is rating column in the dataframe.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 57px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>To learn from our dataset, let's plot two histograms side-by-side, one for No. of ratings for movies, n_ratings column, and the other for average rating which is rating column in the dataframe.</p>
</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 28px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We can creates two subplots and unpacks the output array immediately.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 40px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>We can creates two subplots and unpacks the output array immediately.</p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[13]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 51.5972px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 477.667px; margin-bottom: -16px; border-right-width: 14px; min-height: 146px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.5972px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation" style=""><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">f</span> , (<span class="cm-variable">ax1</span>, <span class="cm-variable">ax2</span>) <span class="cm-operator">=</span> <span class="cm-variable">plt</span>.<span class="cm-property">subplots</span>(<span class="cm-variable">nrows</span><span class="cm-operator">=</span><span class="cm-number">1</span>,<span class="cm-variable">ncols</span><span class="cm-operator">=</span><span class="cm-number">2</span>,<span class="cm-variable">figsize</span><span class="cm-operator">=</span>(<span class="cm-number">10</span>,<span class="cm-number">4</span>))</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">ax1</span>.<span class="cm-property">set_title</span>(<span class="cm-string">'No of ratings'</span>)</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">ax1</span>.<span class="cm-property">hist</span>(<span class="cm-variable">rating</span>[<span class="cm-string">'n_ratings'</span>], <span class="cm-variable">bins</span> <span class="cm-operator">=</span> <span class="cm-number">30</span>)</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">5</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">ax2</span>.<span class="cm-property">set_title</span>(<span class="cm-string">'Rating'</span>)</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">6</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">ax2</span>.<span class="cm-property">hist</span>(<span class="cm-variable">rating</span>[<span class="cm-string">'rating'</span>], <span class="cm-variable">bins</span> <span class="cm-operator">=</span> <span class="cm-number">30</span>)</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">7</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">8</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">plt</span>.<span class="cm-property">show</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 146px;"></div><div class="CodeMirror-gutters" style="height: 160px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt"></div><div class="output_subarea output_png"><img src="data:image/png;base64,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"></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 62px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.4445px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">If we look at the "No. of Ratings" on the left, we learn that most of the movies have 0 or 1 number of ratings! So, either, people have not watched those movies and if they have watched, they did not rate them. The first argument somehow make sense, because, most of the time we prefer to watch only the famous movies.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 62px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 74px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>If we look at the "No. of Ratings" on the left, we learn that most of the movies have 0 or 1 number of ratings! So, either, people have not watched those movies and if they have watched, they did not rate them. The first argument somehow make sense, because, most of the time we prefer to watch only the famous movies.</p>
</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59741px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 96px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>3</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.4445px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">If we look at the "Rating, which is actually the mean rating" on the right, we may find that there are peaks at the whole numbers {1,2,3,4,5}. This is again a usual act, most of the time people rate the things with the whole numbers. </span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Notice, there are some movies with average 5 star rating, they might be the outstanding movies or may got only few ratings. You can also point out some movies with really bad rating. However, most of the movies got average rating between 3 and 4. </span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 96px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 108px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>If we look at the "Rating, which is actually the mean rating" on the right, we may find that there are peaks at the whole numbers {1,2,3,4,5}. This is again a usual act, most of the time people rate the things with the whole numbers. </p>
<p>Notice, there are some movies with average 5 star rating, they might be the outstanding movies or may got only few ratings. You can also point out some movies with really bad rating. However, most of the movies got average rating between 3 and 4. </p>
</div></div></div><div class="cell text_cell unselected rendered collapsible_headings_ellipsis" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h5"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 29px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 17.7778px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-5">##### Let's check the relationship between rating and no. of rating with a seaborn jointplot()</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 29px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 41px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h5 id="Let&#39;s-check-the-relationship-between-rating-and-no.-of-rating-with-a-seaborn-jointplot()">Let's check the relationship between rating and no. of rating with a seaborn jointplot()<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Let&#39;s-check-the-relationship-between-rating-and-no.-of-rating-with-a-seaborn-jointplot()">¶</a></h5>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[14]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59961px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 431.861px; margin-bottom: -16px; border-right-width: 14px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">sns</span>.<span class="cm-property">jointplot</span>(<span class="cm-variable">x</span><span class="cm-operator">=</span><span class="cm-string">'rating'</span>, <span class="cm-variable">y</span> <span class="cm-operator">=</span> <span class="cm-string">'n_ratings'</span>, <span class="cm-variable">data</span><span class="cm-operator">=</span><span class="cm-variable">rating</span>)</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">plt</span>.<span class="cm-property">show</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="height: 59px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt"></div><div class="output_subarea output_text output_stream output_stderr"><pre>C:\Users\Stevy\Anaconda3\lib\site-packages\scipy\stats\stats.py:1713: FutureWarning: Using a non-tuple sequence for multidimensional indexing is deprecated; use `arr[tuple(seq)]` instead of `arr[seq]`. In the future this will be interpreted as an array index, `arr[np.array(seq)]`, which will result either in an error or a different result.
  return np.add.reduce(sorted[indexer] * weights, axis=axis) / sumval
</pre></div></div><div class="output_area"><div class="run_this_cell"></div><div class="prompt"></div><div class="output_subarea output_png"><img src="data:image/png;base64,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"></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 22.0417px; left: 255.111px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><pre><span>xxxxxxxxxx</span></pre></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 221.111px; top: 16.4444px; height: 17.3334px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">The joint plot is is making sense, more the number of rating a movie have, more average rating it gets.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 56px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>The joint plot is is making sense, more the number of rating a movie have, more average rating it gets.</p>
</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 55.8194px; left: 124.264px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 79px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><pre><span>xxxxxxxxxx</span></pre></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 90.2639px; top: 50.2222px; height: 17.3334px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Good the movie is, more people will watch it and the movie will get more number of ratings or reviews. This is a normal act.</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We also see from the plot that the 1 or 2 stars movie have very few number of ratings.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 79px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 90px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>Good the movie is, more people will watch it and the movie will get more number of ratings or reviews. This is a normal act.
We also see from the plot that the 1 or 2 stars movie have very few number of ratings.</p>
</div></div></div><div class="cell text_cell collapsible_headings_ellipsis rendered unselected" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h2"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59723px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 32px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 5.33333px; top: 0px; height: 20.4444px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-2">## Recommender System for similar movie</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 32px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 43px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h2 id="Recommender-System-for-similar-movie" data-toc-modified-id="Recommender-System-for-similar-movie-1.3"><a class="toc-mod-link" id="Recommender-System-for-similar-movie-1.3"></a><span class="toc-item-num">1.3&nbsp;&nbsp;</span>Recommender System for similar movie<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Recommender-System-for-similar-movie">¶</a></h2>
</div></div></div><div class="cell text_cell collapsible_headings_ellipsis rendered unselected" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h5"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 23.375px; left: 114px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 47px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 80px; top: 17.7778px; height: 17.7778px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-5">##### Let's develop a simple recommender system that can recommend similar movies to the user.</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 47px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 58px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h5 id="Let&#39;s-develop-a-simple-recommender-system-that-can-recommend-similar-movies-to-the-user.">Let's develop a simple recommender system that can recommend similar movies to the user.<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Let&#39;s-develop-a-simple-recommender-system-that-can-recommend-similar-movies-to-the-user.">¶</a></h5>
</div></div></div><div class="cell code_cell rendered unselected" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[15]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 113.153px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 77.8472px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><pre><span>xxxxxxxxxx</span></pre></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 67.1528px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">df</span>.<span class="cm-property">head</span><span class=" CodeMirror-matchingbracket">(</span><span class=" CodeMirror-matchingbracket">)</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 42px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[15]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>userId</th>
      <th>movieId</th>
      <th>rating</th>
      <th>timestamp</th>
      <th>title</th>
      <th>genres</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>31</td>
      <td>2.5</td>
      <td>1260759144</td>
      <td>Dangerous Minds (1995)</td>
      <td>Drama</td>
    </tr>
    <tr>
      <th>1</th>
      <td>7</td>
      <td>31</td>
      <td>3.0</td>
      <td>851868750</td>
      <td>Dangerous Minds (1995)</td>
      <td>Drama</td>
    </tr>
    <tr>
      <th>2</th>
      <td>31</td>
      <td>31</td>
      <td>4.0</td>
      <td>1273541953</td>
      <td>Dangerous Minds (1995)</td>
      <td>Drama</td>
    </tr>
    <tr>
      <th>3</th>
      <td>32</td>
      <td>31</td>
      <td>4.0</td>
      <td>834828440</td>
      <td>Dangerous Minds (1995)</td>
      <td>Drama</td>
    </tr>
    <tr>
      <th>4</th>
      <td>36</td>
      <td>31</td>
      <td>3.0</td>
      <td>847057202</td>
      <td>Dangerous Minds (1995)</td>
      <td>Drama</td>
    </tr>
  </tbody>
</table>
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 38.9306px; left: 616.889px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 62px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 582.889px; top: 33.3333px; height: 17.3333px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Let's create a matrix that will have the userId on one axis (index) and the title on another axis (columns) whereas, rating as its value. In the way, each cell will consist of the rating that the user gave to a certain movie.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 62px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 73px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>Let's create a matrix that will have the userId on one axis (index) and the title on another axis (columns) whereas, rating as its value. In the way, each cell will consist of the rating that the user gave to a certain movie.</p>
</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 22.0417px; left: 439.847px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 405.847px; top: 16.4444px; height: 17.3334px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We need userId, title and rating columns for such matrix. We are going to use pivot_table() method to get our required matrix.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 56px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>We need userId, title and rating columns for such matrix. We are going to use pivot_table() method to get our required matrix.</p>
</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59723px; left: 385.958px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 351.958px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Our parameter for the pivot_table() will be: </span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 39px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>Our parameter for the pivot_table() will be: </p>
</div></div></div><div class="cell text_cell unrendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 39.6px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -17px; border-right-width: 13px; min-height: 62px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>3</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style=""><div class="CodeMirror-cursor" style="left: 5.60001px; top: 0px; height: 16.8px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">index = userId</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">columns = title</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">values = rating</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 13px; width: 1px; border-bottom: 0px solid transparent; top: 62px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 75px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"></div></div></div><div class="cell code_cell rendered unselected" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[16]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 528.667px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true" style="display: block; right: 0px; left: 46px;"><div style="height: 100%; min-height: 1px; width: 603px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 601.208px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 16px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 482.667px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">rating_mat</span> <span class="cm-operator">=</span> <span class="cm-variable">df</span>.<span class="cm-property">pivot_table</span>(<span class="cm-variable">values</span><span class="cm-operator">=</span><span class="cm-string">'rating'</span>, <span class="cm-variable">index</span><span class="cm-operator">=</span><span class="cm-string">'userId'</span>, <span class="cm-variable">columns</span><span class="cm-operator">=</span><span class="cm-string">'title'</span>)</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 16px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: -1.90735e-06px; height: 58px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell code_cell rendered unselected" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[17]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 174.736px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 139.431px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><pre><span>xxxxxxxxxx</span></pre></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 128.736px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">rating_mat</span>.<span class="cm-property">head</span><span class=" CodeMirror-matchingbracket">(</span><span class=" CodeMirror-matchingbracket">)</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 42px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[17]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>title</th>
      <th>"Great Performances" Cats (1998)</th>
      <th>$9.99 (2008)</th>
      <th>'Hellboy': The Seeds of Creation (2004)</th>
      <th>'Neath the Arizona Skies (1934)</th>
      <th>'Round Midnight (1986)</th>
      <th>'Salem's Lot (2004)</th>
      <th>'Til There Was You (1997)</th>
      <th>'burbs, The (1989)</th>
      <th>'night Mother (1986)</th>
      <th>(500) Days of Summer (2009)</th>
      <th>...</th>
      <th>Zulu (1964)</th>
      <th>Zulu (2013)</th>
      <th>[REC] (2007)</th>
      <th>eXistenZ (1999)</th>
      <th>loudQUIETloud: A Film About the Pixies (2006)</th>
      <th>xXx (2002)</th>
      <th>xXx: State of the Union (2005)</th>
      <th>¡Three Amigos! (1986)</th>
      <th>À nous la liberté (Freedom for Us) (1931)</th>
      <th>İtirazım Var (2014)</th>
    </tr>
    <tr>
      <th>userId</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 9064 columns</p>
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell collapsible_headings_ellipsis rendered unselected" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h5"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59723px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 29px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33333px; top: 0px; height: 17.7778px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-5">##### Let's check the most rated movies once again from our rating dataframne.</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 29px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 40px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h5 id="Let&#39;s-check-the-most-rated-movies-once-again-from-our-rating-dataframne.">Let's check the most rated movies once again from our rating dataframne.<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Let&#39;s-check-the-most-rated-movies-once-again-from-our-rating-dataframne.">¶</a></h5>
</div></div></div><div class="cell code_cell rendered unselected" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[18]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59985px; left: 490.278px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 447.278px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style=""><div class="CodeMirror-cursor" style="left: 444.278px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">rating</span>.<span class="cm-property">sort_values</span>(<span class="cm-string">'n_ratings'</span>, <span class="cm-variable">ascending</span><span class="cm-operator">=</span><span class="cm-keyword">False</span>).<span class="cm-property">head</span><span class=" CodeMirror-matchingbracket">(</span><span class="cm-number">10</span><span class=" CodeMirror-matchingbracket">)</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 42px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[18]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>rating</th>
      <th>n_ratings</th>
    </tr>
    <tr>
      <th>title</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Forrest Gump (1994)</th>
      <td>4.054252</td>
      <td>341</td>
    </tr>
    <tr>
      <th>Pulp Fiction (1994)</th>
      <td>4.256173</td>
      <td>324</td>
    </tr>
    <tr>
      <th>Shawshank Redemption, The (1994)</th>
      <td>4.487138</td>
      <td>311</td>
    </tr>
    <tr>
      <th>Silence of the Lambs, The (1991)</th>
      <td>4.138158</td>
      <td>304</td>
    </tr>
    <tr>
      <th>Star Wars: Episode IV - A New Hope (1977)</th>
      <td>4.221649</td>
      <td>291</td>
    </tr>
    <tr>
      <th>Jurassic Park (1993)</th>
      <td>3.706204</td>
      <td>274</td>
    </tr>
    <tr>
      <th>Matrix, The (1999)</th>
      <td>4.183398</td>
      <td>259</td>
    </tr>
    <tr>
      <th>Toy Story (1995)</th>
      <td>3.872470</td>
      <td>247</td>
    </tr>
    <tr>
      <th>Schindler's List (1993)</th>
      <td>4.303279</td>
      <td>244</td>
    </tr>
    <tr>
      <th>Terminator 2: Judgment Day (1991)</th>
      <td>4.006329</td>
      <td>237</td>
    </tr>
  </tbody>
</table>
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell code_cell rendered unselected" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[21]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 244.222px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1" draggable="false"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 362.639px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><pre>x</pre></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"><div class="CodeMirror-selected" style="position: absolute; left: 198.222px; top: 0px; width: 145.778px; height: 17px;"></div></div><div class="CodeMirror-cursors" style=""></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">movies</span>[<span class="cm-variable">movies</span>[<span class="cm-string">'title'</span>]<span class="cm-operator">==</span><span class="cm-string">'Forrest Gump (1994)'</span>]</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 42px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[21]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movieId</th>
      <th>title</th>
      <th>genres</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>321</th>
      <td>356</td>
      <td>Forrest Gump (1994)</td>
      <td>Comedy|Drama|Romance|War</td>
    </tr>
  </tbody>
</table>
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell code_cell rendered unselected" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[22]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59985px; left: 397.944px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 354.917px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style=""><div class="CodeMirror-cursor" style="left: 351.944px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">movies</span><span class=" CodeMirror-matchingbracket">[</span><span class="cm-variable">movies</span>[<span class="cm-string">'title'</span>]<span class="cm-operator">==</span><span class="cm-string">'Matrix, The (1999)'</span><span class=" CodeMirror-matchingbracket">]</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 42px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[22]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>movieId</th>
      <th>title</th>
      <th>genres</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2062</th>
      <td>2571</td>
      <td>Matrix, The (1999)</td>
      <td>Action|Sci-Fi|Thriller</td>
    </tr>
  </tbody>
</table>
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell code_cell rendered unselected" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[25]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 22.3999px; left: 197.833px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 424.222px; margin-bottom: -16px; border-right-width: 14px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>2</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 151.833px; top: 16.8px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">FG_user_ratings</span> <span class="cm-operator">=</span> <span class="cm-variable">rating_mat</span>[<span class="cm-string">'Forrest Gump (1994)'</span>]</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">Matrix_user_ratings</span> <span class="cm-operator">=</span> <span class="cm-variable">rating_mat</span>[<span class="cm-string">'Matrix, The (1999)'</span>]</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 59px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell code_cell rendered unselected" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[26]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59998px; left: 382.542px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 393.222px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style=""><div class="CodeMirror-cursor" style="left: 336.542px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">FG_user_ratings</span>.<span class="cm-property">head</span>(), <span class="cm-variable">Matrix_user_ratings</span>.<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 42px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[26]:</bdi></div><div class="output_subarea output_text output_result"><pre>(userId
 1    NaN
 2    3.0
 3    5.0
 4    5.0
 5    4.0
 Name: Forrest Gump (1994), dtype: float64, userId
 1   NaN
 2   NaN
 3   NaN
 4   NaN
 5   NaN
 Name: Matrix, The (1999), dtype: float64)</pre></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 38.9305px; left: 155.042px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 62px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>2</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 121.042px; top: 33.3333px; height: 17.3333px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">we got the user ratings for the selected movies. </span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Now, we want to know how these movies are correlated to the other movies in the dataframe. </span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 62px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 73px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>we got the user ratings for the selected movies. 
Now, we want to know how these movies are correlated to the other movies in the dataframe. </p>
</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 22.0417px; left: 578px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><pre><span>xxxxxxxxxx</span></pre></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 544px; top: 16.4444px; height: 17.3334px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Let's see how the user rating of Forrest Gump (FG_user_ratings) is correlated with the user rating of all other movies in the rating_mat.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 56px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>Let's see how the user rating of Forrest Gump (FG_user_ratings) is correlated with the user rating of all other movies in the rating_mat.</p>
</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 38.9306px; left: 324.389px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 62px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><pre><span>xxxxxxxxxx</span></pre></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 290.389px; top: 33.3333px; height: 17.3333px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We are going to compute the correlation of FG_user_ratings to the user rating or user behavior for all other movies and passing that to similar_to_FG and  similar_to_Matrix.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 62px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 73px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>We are going to compute the correlation of FG_user_ratings to the user rating or user behavior for all other movies and passing that to similar_to_FG and  similar_to_Matrix.</p>
</div></div></div><div class="cell code_cell rendered unselected" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[31]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 22.4px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 462.694px; margin-bottom: -16px; border-right-width: 14px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><pre>x</pre></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"><div class="CodeMirror-selected" style="position: absolute; left: 5.33333px; top: 17px; width: 131.111px; height: 17px;"></div></div><div class="CodeMirror-cursors" style="visibility: hidden;"></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">similar_to_FG</span> <span class="cm-operator">=</span> <span class="cm-variable">rating_mat</span>.<span class="cm-property">corrwith</span>(<span class="cm-variable">FG_user_ratings</span>)</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">similar_to_Matrix</span> <span class="cm-operator">=</span><span class="cm-variable">rating_mat</span>.<span class="cm-property">corrwith</span>(<span class="cm-variable">Matrix_user_ratings</span>)</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 59px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt"></div><div class="output_subarea output_text output_stream output_stderr"><pre>C:\Users\Stevy\Anaconda3\lib\site-packages\numpy\lib\function_base.py:2392: RuntimeWarning: Degrees of freedom &lt;= 0 for slice
  c = cov(x, y, rowvar)
C:\Users\Stevy\Anaconda3\lib\site-packages\numpy\lib\function_base.py:2326: RuntimeWarning: divide by zero encountered in true_divide
  c *= np.true_divide(1, fact)
</pre></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unrendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59998px; left: 186px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -17px; border-right-width: 13px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 152px; top: 0px; height: 16.8px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">similar_to_FG.head()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 13px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 41px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>Type <em>Markdown</em> and LaTeX: <span class="MathJax_Preview" style="color: inherit; display: none;"></span><span class="MathJax" id="MathJax-Element-16-Frame" tabindex="0" data-mathml="&lt;math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;&gt;&lt;msup&gt;&lt;mi&gt;&amp;#x03B1;&lt;/mi&gt;&lt;mn&gt;2&lt;/mn&gt;&lt;/msup&gt;&lt;/math&gt;" role="presentation" style="position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-76" style="width: 1.157em; display: inline-block;"><span style="display: inline-block; position: relative; width: 0.965em; height: 0px; font-size: 120%;"><span style="position: absolute; clip: rect(1.221em, 1000.97em, 2.439em, -999.997em); top: -2.24em; left: 0em;"><span class="mrow" id="MathJax-Span-77"><span class="msubsup" id="MathJax-Span-78"><span style="display: inline-block; position: relative; width: 0.965em; height: 0px;"><span style="position: absolute; clip: rect(3.337em, 1000.58em, 4.17em, -999.997em); top: -3.971em; left: 0em;"><span class="mi" id="MathJax-Span-79" style="font-family: STIXMathJax_Main-italic;">α</span><span style="display: inline-block; width: 0px; height: 3.978em;"></span></span><span style="position: absolute; top: -4.356em; left: 0.58em;"><span class="mn" id="MathJax-Span-80" style="font-size: 70.7%; font-family: STIXMathJax_Main;">2</span><span style="display: inline-block; width: 0px; height: 3.978em;"></span></span></span></span></span><span style="display: inline-block; width: 0px; height: 2.247em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.073em; border-left: 0px solid; width: 0px; height: 1.158em;"></span></span></nobr><span class="MJX_Assistive_MathML" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML"><msup><mi>α</mi><mn>2</mn></msup></math></span></span><script type="math/tex" id="MathJax-Element-16">\alpha^2</script></p>
</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59723px; left: 478.333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><pre><span>xxxxxxxxxx</span></pre></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style=""><div class="CodeMirror-cursor" style="left: 444.333px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We need to clean the data for null value using dropna(). </span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 39px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>We need to clean the data for null value using dropna(). </p>
</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 22.0417px; left: 331.778px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><pre><span>xxxxxxxxxx</span></pre></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style=""><div class="CodeMirror-cursor" style="left: 297.778px; top: 16.4444px; height: 17.3333px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">First, We can create a dataframe instead of series so that it look little nicer, and then we will deal with NaN.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 56px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>First, We can create a dataframe instead of series so that it look little nicer, and then we will deal with NaN.</p>
</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 38.9306px; left: 131.778px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 62px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><pre><span>xxxxxxxxxx</span></pre></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style=""><div class="CodeMirror-cursor" style="left: 97.7778px; top: 33.3333px; height: 17.3333px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">In order to create a dataframe, we need to pass similar_to_FG and similar_to_matrix to pandas DataFrame(). We can set the column name as correlation.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 62px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 73px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>In order to create a dataframe, we need to pass similar_to_FG and similar_to_matrix to pandas DataFrame(). We can set the column name as correlation.</p>
</div></div></div><div class="cell code_cell rendered unselected" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[32]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 22.4px; left: 159.333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 485.667px; margin-bottom: -16px; border-right-width: 14px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>2</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 113.333px; top: 16.8px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">corr_FG</span> <span class="cm-operator">=</span> <span class="cm-variable">pd</span>.<span class="cm-property">DataFrame</span>(<span class="cm-variable">similar_to_FG</span>, <span class="cm-variable">columns</span><span class="cm-operator">=</span>[<span class="cm-string">'correlation'</span>])</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">corr_FG</span>.<span class="cm-property">head</span><span class=" CodeMirror-matchingbracket">(</span><span class=" CodeMirror-matchingbracket">)</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 59px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[32]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>correlation</th>
    </tr>
    <tr>
      <th>title</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>"Great Performances" Cats (1998)</th>
      <td>NaN</td>
    </tr>
    <tr>
      <th>$9.99 (2008)</th>
      <td>1.0</td>
    </tr>
    <tr>
      <th>'Hellboy': The Seeds of Creation (2004)</th>
      <td>NaN</td>
    </tr>
    <tr>
      <th>'Neath the Arizona Skies (1934)</th>
      <td>NaN</td>
    </tr>
    <tr>
      <th>'Round Midnight (1986)</th>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell collapsible_headings_ellipsis rendered unselected" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h5"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59723px; left: 314.889px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 29px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style=""><div class="CodeMirror-cursor" style="left: 280.889px; top: 0px; height: 17.7778px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-5">##### Let's drop NaN and check the head</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 29px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 40px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h5 id="Let&#39;s-drop-NaN-and-check-the-head">Let's drop NaN and check the head<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Let&#39;s-drop-NaN-and-check-the-head">¶</a></h5>
</div></div></div><div class="cell text_cell unrendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.60004px; left: 262.8px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -17px; border-right-width: 13px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>2</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 228.8px; top: 0px; height: 16.8px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">corr_FG.dropna(inplace = True)</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">corr_FG.head()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 13px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 58px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>Type <em>Markdown</em> and LaTeX: <span class="MathJax_Preview" style="color: inherit; display: none;"></span><span class="MathJax" id="MathJax-Element-20-Frame" tabindex="0" data-mathml="&lt;math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;&gt;&lt;msup&gt;&lt;mi&gt;&amp;#x03B1;&lt;/mi&gt;&lt;mn&gt;2&lt;/mn&gt;&lt;/msup&gt;&lt;/math&gt;" role="presentation" style="position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-96" style="width: 1.157em; display: inline-block;"><span style="display: inline-block; position: relative; width: 0.965em; height: 0px; font-size: 120%;"><span style="position: absolute; clip: rect(1.221em, 1000.97em, 2.439em, -999.997em); top: -2.24em; left: 0em;"><span class="mrow" id="MathJax-Span-97"><span class="msubsup" id="MathJax-Span-98"><span style="display: inline-block; position: relative; width: 0.965em; height: 0px;"><span style="position: absolute; clip: rect(3.337em, 1000.58em, 4.17em, -999.997em); top: -3.971em; left: 0em;"><span class="mi" id="MathJax-Span-99" style="font-family: STIXMathJax_Main-italic;">α</span><span style="display: inline-block; width: 0px; height: 3.978em;"></span></span><span style="position: absolute; top: -4.356em; left: 0.58em;"><span class="mn" id="MathJax-Span-100" style="font-size: 70.7%; font-family: STIXMathJax_Main;">2</span><span style="display: inline-block; width: 0px; height: 3.978em;"></span></span></span></span></span><span style="display: inline-block; width: 0px; height: 2.247em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.073em; border-left: 0px solid; width: 0px; height: 1.158em;"></span></span></nobr><span class="MJX_Assistive_MathML" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML"><msup><mi>α</mi><mn>2</mn></msup></math></span></span><script type="math/tex" id="MathJax-Element-20">\alpha^2</script></p>
</div></div></div><div class="cell text_cell collapsible_headings_ellipsis rendered unselected" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h5"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59723px; left: 267.778px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 29px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 233.778px; top: 0px; height: 17.7778px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-5">##### Let's do the same for Matrix</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 29px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 40px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h5 id="Let&#39;s-do-the-same-for-Matrix">Let's do the same for Matrix<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Let&#39;s-do-the-same-for-Matrix">¶</a></h5>
</div></div></div><div class="cell text_cell unrendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 22.4px; left: 278px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -17px; border-right-width: 13px; min-height: 62px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>3</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 244px; top: 16.8px; height: 16.8px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">corr_matrix = pd.DataFrame(similar_to_Matrix, columns=<span class="cm-link">['correlation']</span>)</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">corr_matrix.dropna(inplace = True)</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">corr_matrix.head()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 13px; width: 1px; border-bottom: 0px solid transparent; top: 62px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 75px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>Type <em>Markdown</em> and LaTeX: <span class="MathJax_Preview" style="color: inherit; display: none;"></span><span class="MathJax" id="MathJax-Element-22-Frame" tabindex="0" data-mathml="&lt;math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;&gt;&lt;msup&gt;&lt;mi&gt;&amp;#x03B1;&lt;/mi&gt;&lt;mn&gt;2&lt;/mn&gt;&lt;/msup&gt;&lt;/math&gt;" role="presentation" style="position: relative;"><nobr aria-hidden="true"><span class="math" id="MathJax-Span-106" style="width: 1.157em; display: inline-block;"><span style="display: inline-block; position: relative; width: 0.965em; height: 0px; font-size: 120%;"><span style="position: absolute; clip: rect(1.221em, 1000.97em, 2.439em, -999.997em); top: -2.24em; left: 0em;"><span class="mrow" id="MathJax-Span-107"><span class="msubsup" id="MathJax-Span-108"><span style="display: inline-block; position: relative; width: 0.965em; height: 0px;"><span style="position: absolute; clip: rect(3.337em, 1000.58em, 4.17em, -999.997em); top: -3.971em; left: 0em;"><span class="mi" id="MathJax-Span-109" style="font-family: STIXMathJax_Main-italic;">α</span><span style="display: inline-block; width: 0px; height: 3.978em;"></span></span><span style="position: absolute; top: -4.356em; left: 0.58em;"><span class="mn" id="MathJax-Span-110" style="font-size: 70.7%; font-family: STIXMathJax_Main;">2</span><span style="display: inline-block; width: 0px; height: 3.978em;"></span></span></span></span></span><span style="display: inline-block; width: 0px; height: 2.247em;"></span></span></span><span style="display: inline-block; overflow: hidden; vertical-align: -0.073em; border-left: 0px solid; width: 0px; height: 1.158em;"></span></span></nobr><span class="MJX_Assistive_MathML" role="presentation"><math xmlns="http://www.w3.org/1998/Math/MathML"><msup><mi>α</mi><mn>2</mn></msup></math></span></span><script type="math/tex" id="MathJax-Element-22">\alpha^2</script></p>
</div></div></div><div class="cell text_cell collapsible_headings_ellipsis rendered unselected" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h5"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59723px; left: 189.556px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 29px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style=""><div class="CodeMirror-cursor" style="left: 155.556px; top: 0px; height: 17.7778px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-5">##### Let's sort Matrix</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 29px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 40px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h5 id="Let&#39;s-sort-Matrix">Let's sort Matrix<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Let&#39;s-sort-Matrix">¶</a></h5>
</div></div></div><div class="cell code_cell rendered unselected" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[38]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59998px; left: 528.764px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 485.764px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style=""><div class="CodeMirror-cursor" style="left: 482.764px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">corr_matrix</span>.<span class="cm-property">sort_values</span>(<span class="cm-string">'correlation'</span>, <span class="cm-variable">ascending</span><span class="cm-operator">=</span><span class="cm-keyword">False</span>).<span class="cm-property">head</span><span class=" CodeMirror-matchingbracket">(</span><span class=" CodeMirror-matchingbracket">)</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 42px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[38]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>correlation</th>
    </tr>
    <tr>
      <th>title</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Project X (2012)</th>
      <td>1.0</td>
    </tr>
    <tr>
      <th>Southland Tales (2006)</th>
      <td>1.0</td>
    </tr>
    <tr>
      <th>Savages (2012)</th>
      <td>1.0</td>
    </tr>
    <tr>
      <th>Escape from Alcatraz (1979)</th>
      <td>1.0</td>
    </tr>
    <tr>
      <th>Umbrellas of Cherbourg, The (Parapluies de Cherbourg, Les) (1964)</th>
      <td>1.0</td>
    </tr>
  </tbody>
</table>
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 22.0417px; left: 516.819px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style=""><div class="CodeMirror-cursor" style="left: 482.819px; top: 16.4445px; height: 17.3333px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We may not have ever heard about most of these movies but the correlation that we got is perfect. The results does not make much sense. </span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 56px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>We may not have ever heard about most of these movies but the correlation that we got is perfect. The results does not make much sense. </p>
</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 38.9305px; left: 270.444px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 62px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style=""><div class="CodeMirror-cursor" style="left: 236.444px; top: 33.3333px; height: 17.3334px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We need to fix this and we know what the reason is. Most likely, these movies are watched only once by the same users who also watched Matrix and rated both with similar stars.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 62px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 73px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>We need to fix this and we know what the reason is. Most likely, these movies are watched only once by the same users who also watched Matrix and rated both with similar stars.</p>
</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 38.9306px; left: 301.292px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 62px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><pre><span>xxxxxxxxxx</span></pre></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 267.292px; top: 33.3333px; height: 17.3333px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">To fix this, we can set a threshold value for the ratings.</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Let's re-plot a histogram for n_rating to see which could be a good threshold value for no of ratings.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 62px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 73px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>To fix this, we can set a threshold value for the ratings.
Let's re-plot a histogram for n_rating to see which could be a good threshold value for no of ratings.</p>
</div></div></div><div class="cell code_cell rendered unselected" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[40]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 22.4px; left: 128.542px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 316.417px; margin-bottom: -16px; border-right-width: 14px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>2</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 82.5417px; top: 16.8px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">plt</span>.<span class="cm-property">hist</span>(<span class="cm-variable">rating</span>[<span class="cm-string">'n_ratings'</span>], <span class="cm-variable">bins</span> <span class="cm-operator">=</span> <span class="cm-number">50</span>)</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">plt</span>.<span class="cm-property">show</span><span class=" CodeMirror-matchingbracket">(</span><span class=" CodeMirror-matchingbracket">)</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 59px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt"></div><div class="output_subarea output_png"><img src="data:image/png;base64,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"></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59723px; left: 501.431px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 467.431px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We can see that the drop is significant after n_rating = 50.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 39px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>We can see that the drop is significant after n_rating = 50.</p>
</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 22.0417px; left: 216.222px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><pre><span>xxxxxxxxxx</span></pre></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style=""><div class="CodeMirror-cursor" style="left: 182.222px; top: 16.4444px; height: 17.3334px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We can select 50 as a minimum no. of rating in order to be considered into our recommender system.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 56px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>We can select 50 as a minimum no. of rating in order to be considered into our recommender system.</p>
</div></div></div><div class="cell text_cell collapsible_headings_ellipsis rendered unselected" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h5"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 41.1528px; left: 215.778px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 65px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 181.778px; top: 35.5556px; height: 17.7778px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-5">##### Let's sort the value again with the condition (n_rating &gt;50) and also join the n_ratings column from rating dataframe to corr_matrix dataframe and apply the condition for n_rating &gt; 50</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 65px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 76px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h5 id="Let&#39;s-sort-the-value-again-with-the-condition-(n_rating-&gt;50)-and-also-join-the-n_ratings-column-from-rating-dataframe-to-corr_matrix-dataframe-and-apply-the-condition-for-n_rating-&gt;-50">Let's sort the value again with the condition (n_rating &gt;50) and also join the n_ratings column from rating dataframe to corr_matrix dataframe and apply the condition for n_rating &gt; 50<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Let&#39;s-sort-the-value-again-with-the-condition-(n_rating-%3E50)-and-also-join-the-n_ratings-column-from-rating-dataframe-to-corr_matrix-dataframe-and-apply-the-condition-for-n_rating-%3E-50">¶</a></h5>
</div></div></div><div class="cell code_cell rendered unselected" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[41]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 22.4px; left: 190.125px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 401.111px; margin-bottom: -16px; border-right-width: 14px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>2</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 144.125px; top: 16.8px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">corr_matrix</span> <span class="cm-operator">=</span> <span class="cm-variable">corr_matrix</span>.<span class="cm-property">join</span>(<span class="cm-variable">rating</span>[<span class="cm-string">'n_ratings'</span>])</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">corr_matrix</span>.<span class="cm-property">head</span><span class=" CodeMirror-matchingbracket">(</span><span class=" CodeMirror-matchingbracket">)</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 59px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[41]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>correlation</th>
      <th>n_ratings</th>
    </tr>
    <tr>
      <th>title</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>$9.99 (2008)</th>
      <td>1.000000</td>
      <td>3</td>
    </tr>
    <tr>
      <th>'burbs, The (1989)</th>
      <td>0.056624</td>
      <td>19</td>
    </tr>
    <tr>
      <th>(500) Days of Summer (2009)</th>
      <td>0.368837</td>
      <td>45</td>
    </tr>
    <tr>
      <th>*batteries not included (1987)</th>
      <td>0.743955</td>
      <td>7</td>
    </tr>
    <tr>
      <th>...And Justice for All (1979)</th>
      <td>-0.610170</td>
      <td>13</td>
    </tr>
  </tbody>
</table>
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell collapsible_headings_ellipsis rendered unselected" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h5"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59723px; left: 386px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -19px; border-right-width: 11px; min-height: 29px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 352px; top: 0px; height: 17.7778px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-5">##### Let's sort the values in order from high to low</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 11px; width: 1px; border-bottom: 0px solid transparent; top: 29px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 40px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h5 id="Let&#39;s-sort-the-values-in-order-from-high-to-low">Let's sort the values in order from high to low<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Let&#39;s-sort-the-values-in-order-from-high-to-low">¶</a></h5>
</div></div></div><div class="cell code_cell rendered unselected" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[&nbsp;]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.60001px; left: 606px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true" style="display: block; right: 0px; left: 46px;"><div style="height: 100%; min-height: 1px; width: 725px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 724.288px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 16px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 698.4px; top: 0px; height: 16.8px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: 107.6px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">corr_matrix</span>[<span class="cm-variable">corr_matrix</span>[<span class="cm-string">'n_ratings'</span>]<span class="cm-operator">&gt;</span><span class="cm-number">50</span>].<span class="cm-property">sort_values</span>(<span class="cm-string">'correlation'</span>, <span class="cm-variable">ascending</span> <span class="cm-operator">=</span> <span class="cm-keyword">False</span>).<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 16px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 153.6px; height: 58px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 22px; left: 501.2px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -17px; border-right-width: 13px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style=""><div class="CodeMirror-cursor" style="left: 467.2px; top: 16.4px; height: 17.2px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">The results make much more sense! Matrix has the perfect correlation to itself. The Star Trek is the closely correlated with Matrix.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 13px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="left: 7.62939e-06px; height: 58px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>The results make much more sense! Matrix has the perfect correlation to itself. The Star Trek is the closely correlated with Matrix.</p>
</div></div></div><div class="cell text_cell collapsible_headings_ellipsis rendered unselected" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h5"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.60001px; left: 318.8px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; margin-bottom: -17px; border-right-width: 13px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 284.8px; top: 0px; height: 16.8px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-5">##### Let's do the same for Forrest Gump</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 13px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 7.62939e-06px; height: 41px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h5 id="Let&#39;s-do-the-same-for-Forrest-Gump">Let's do the same for Forrest Gump<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#Let&#39;s-do-the-same-for-Forrest-Gump">¶</a></h5>
</div></div></div><div class="cell code_cell rendered selected" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[44]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 39.2px; left: 390.2px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 354.887px; margin-bottom: -16px; border-right-width: 14px; min-height: 62px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>3</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 344.2px; top: 33.6px; height: 16.8px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">corr_FG</span> <span class="cm-operator">=</span> <span class="cm-variable">corr_FG</span>.<span class="cm-property">join</span>(<span class="cm-variable">rating</span>[<span class="cm-string">'n_ratings'</span>])</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div><div class="CodeMirror-gutter-elt" style="left: 33px; width: 13px;"><div class="CodeMirror-foldgutter-open CodeMirror-guttermarker-subtle"></div></div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">corr_FG</span>[<span class="cm-variable">corr_FG</span>[<span class="cm-string">'n_ratings'</span>]<span class="cm-operator">&gt;</span><span class="cm-number">50</span>].<span class="cm-property">sort_values</span>(</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">    <span class="cm-string">'correlation'</span>, <span class="cm-variable">ascending</span> <span class="cm-operator">=</span> <span class="cm-keyword">False</span>).<span class="cm-property">head</span><span class=" CodeMirror-matchingbracket">(</span><span class=" CodeMirror-matchingbracket">)</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 62px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 76px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[44]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>
<style scoped="">
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>correlation</th>
      <th>n_ratings</th>
    </tr>
    <tr>
      <th>title</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Forrest Gump (1994)</th>
      <td>1.000000</td>
      <td>341</td>
    </tr>
    <tr>
      <th>My Big Fat Greek Wedding (2002)</th>
      <td>0.626240</td>
      <td>51</td>
    </tr>
    <tr>
      <th>Beautiful Mind, A (2001)</th>
      <td>0.575922</td>
      <td>114</td>
    </tr>
    <tr>
      <th>Few Good Men, A (1992)</th>
      <td>0.555206</td>
      <td>76</td>
    </tr>
    <tr>
      <th>Million Dollar Baby (2004)</th>
      <td>0.545638</td>
      <td>65</td>
    </tr>
  </tbody>
</table>
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell code_cell unrendered unselected" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[&nbsp;]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59998px; left: 51.6px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 8.60001px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style="visibility: hidden;"><div class="CodeMirror-cursor" style="left: 5.60001px; top: 0px; height: 16.8px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 42px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div></div><div class="end_space"></div></div>
        <div id="tooltip" class="ipython_tooltip" style="display:none"><div class="tooltipbuttons"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#" role="button" class="ui-button"><span class="ui-icon ui-icon-close">Close</span></a><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#" class="ui-corner-all" role="button" id="expanbutton" title="Grow the tooltip vertically (press shift-tab twice)"><span class="ui-icon ui-icon-plus">Expand</span></a><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#" role="button" class="ui-button" title="show the current docstring in pager (press shift-tab 4 times)"><span class="ui-icon ui-icon-arrowstop-l-n">Open in Pager</span></a><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#" role="button" class="ui-button" title="Tooltip will linger for 10 seconds while you type" style="display: none;"><span class="ui-icon ui-icon-clock">Close</span></a></div><div class="pretooltiparrow"></div><div class="tooltiptext smalltooltip"></div></div>
    </div>
</div>



</div>



<div id="pager" class="ui-resizable">
    <div id="pager-contents">
        <div id="pager-container" class="container"></div>
    </div>
    <div id="pager-button-area"><a role="button" title="Open the pager in an external window" class="ui-button"><span class="ui-icon ui-icon-extlink"></span></a><a role="button" title="Close the pager" class="ui-button"><span class="ui-icon ui-icon-close"></span></a></div>
<div class="ui-resizable-handle ui-resizable-n" style="z-index: 90;"></div></div>






<script type="text/javascript">
    sys_info = {"notebook_version": "5.6.0", "notebook_path": "C:\\Users\\Stevy\\Anaconda3\\lib\\site-packages\\notebook", "commit_source": "", "commit_hash": "", "sys_version": "3.7.0 (default, Jun 28 2018, 08:04:48) [MSC v.1912 64 bit (AMD64)]", "sys_executable": "C:\\Users\\Stevy\\Anaconda3\\python.exe", "sys_platform": "win32", "platform": "Windows-10-10.0.17134-SP0", "os_name": "nt", "default_encoding": "utf-8"};
</script>

<script src="./README_files/encoding.js.download" charset="utf-8"></script>

<script src="./README_files/main.min.js.download" type="text/javascript" charset="utf-8"></script>



<script type="text/javascript">
  function _remove_token_from_url() {
    if (window.location.search.length <= 1) {
      return;
    }
    var search_parameters = window.location.search.slice(1).split('&');
    for (var i = 0; i < search_parameters.length; i++) {
      if (search_parameters[i].split('=')[0] === 'token') {
        // remote token from search parameters
        search_parameters.splice(i, 1);
        var new_search = '';
        if (search_parameters.length) {
          new_search = '?' + search_parameters.join('&');
        }
        var new_url = window.location.origin + 
                      window.location.pathname + 
                      new_search + 
                      window.location.hash;
        window.history.replaceState({}, "", new_url);
        return;
      }
    }
  }
  _remove_token_from_url();
</script>


<div style="position: absolute; width: 0px; height: 0px; overflow: hidden; padding: 0px; border: 0px; margin: 0px;"><div id="MathJax_Font_Test" style="position: absolute; visibility: hidden; top: 0px; left: 0px; width: auto; min-width: 0px; max-width: none; padding: 0px; border: 0px; margin: 0px; white-space: nowrap; text-align: left; text-indent: 0px; text-transform: none; line-height: normal; letter-spacing: normal; word-spacing: normal; font-size: 40px; font-weight: normal; font-style: normal; font-family: STIXMathJax_Main, sans-serif;"></div></div><style>#toc li > span:hover { background-color: #DAA520 }
.toc-item-highlight-select  {background-color: #FFD700}
.toc-item-highlight-execute  {background-color: #FF0000}
.toc-item-highlight-execute.toc-item-highlight-select   {background-color: #FFD700}div#menubar-container, div#header-container {
width: auto;
padding-left: 20px; }#toc-wrapper { background-color: #FFFFFF}
#toc a, #navigate_menu a, .toc { color: #333333}#toc-wrapper .toc-item-num { color: #000000}.sidebar-wrapper { border-color: #EEEEEE}.highlight_on_scroll { border-left: solid 4px #2447f0}</style><div id="varInspector-wrapper" class="ui-draggable ui-resizable varInspector-float-wrapper" style="position: fixed; display: none; max-height: 653px;"><div id="varInspector-header" class="header">Variable Inspector <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#" class="kill-btn" title="Close window">[x]</a><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#" class="hide-btn" title="Hide Variable Inspector">[-]</a><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/Recommander_Systems_Project.ipynb#" class="reload-btn" title="Reload Variable Inspector">  ↻</a><span>&nbsp;&nbsp;</span><span>&nbsp;&nbsp;</span></div><div id="varInspector" class="varInspector" style="height: 92.222px; max-height: 633px;"><div class="inspector"><table class="table fixed table-condensed table-nonfluid tablesorter tablesorter-default" role="grid"><colgroup><col>  <col><col></colgroup><thead><tr role="row" class="tablesorter-headerRow"><th data-column="0" class="tablesorter-header tablesorter-headerUnSorted" tabindex="0" scope="col" role="columnheader" aria-disabled="false" unselectable="on" aria-sort="none" aria-label="X: No sort applied, activate to apply an ascending sort" style="user-select: none;"><div class="tablesorter-header-inner">X</div></th><th data-column="1" class="tablesorter-header tablesorter-headerUnSorted" tabindex="0" scope="col" role="columnheader" aria-disabled="false" unselectable="on" aria-sort="none" aria-label="Name: No sort applied, activate to apply an ascending sort" style="user-select: none;"><div class="tablesorter-header-inner">Name</div></th><th data-column="2" class="tablesorter-header tablesorter-headerUnSorted" tabindex="0" scope="col" role="columnheader" aria-disabled="false" unselectable="on" aria-sort="none" aria-label="Type: No sort applied, activate to apply an ascending sort" style="user-select: none;"><div class="tablesorter-header-inner">Type</div></th><th data-column="3" class="tablesorter-header tablesorter-headerUnSorted" tabindex="0" scope="col" role="columnheader" aria-disabled="false" unselectable="on" aria-sort="none" aria-label="Size: No sort applied, activate to apply an ascending sort" style="user-select: none;"><div class="tablesorter-header-inner">Size</div></th><th data-column="4" class="tablesorter-header tablesorter-headerUnSorted" tabindex="0" scope="col" role="columnheader" aria-disabled="false" unselectable="on" aria-sort="none" aria-label="Value: No sort applied, activate to apply an ascending sort" style="user-select: none;"><div class="tablesorter-header-inner">Value</div></th></tr></thead><tbody aria-live="polite" aria-relevant="all"><tr role="row"><td>  </td></tr></tbody></table></div></div><div class="ui-resizable-handle ui-resizable-e" style="z-index: 90;"></div><div class="ui-resizable-handle ui-resizable-s" style="z-index: 90;"></div><div class="ui-resizable-handle ui-resizable-se ui-icon ui-icon-gripsmall-diagonal-se" style="z-index: 90;"></div></div><div class="modal cmd-palette" style="display: none;"><div class="modal-dialog"><div class="modal-content"><div class="modal-body"><form><div class="typeahead-container"><div class="typeahead-field"><span class="typeahead-query" style="position: relative;"><input type="search"><input type="search" readonly="readonly" unselectable="on" tabindex="-1" class="typeahead-hint" style="border-color: transparent; position: absolute; top: 0px; display: inline; z-index: -1; float: none; color: rgb(192, 192, 192); box-shadow: none; cursor: default; user-select: none;"></span><span class="typeahead-button"><button type="submit"><span class="typeahead-search-icon"></span></button></span></div><div class="typeahead-result"><ul class="typeahead-list"><li class="typeahead-group" data-search-group="jupyter-notebook"><a href="javascript:;">jupyter-notebook command group</a></li><li class="active"><a href="javascript:;" data-group="jupyter-notebook" data-index="0"><i class="fa fa-icon {{icon}}"></i><strong>change cell to heading 2</strong>  <div title="jupyter-notebook:change-cell-to-heading-2" class="pull-right command-shortcut"><kbd>2</kbd></div></a></li></ul></div></div></form></div></div></div></div><div class="modal cmd-palette" style="display: none;"><div class="modal-dialog"><div class="modal-content"><div class="modal-body"><form><div class="typeahead-container"><div class="typeahead-field"><span class="typeahead-query" style="position: relative;"><input type="search"><input type="search" readonly="readonly" unselectable="on" tabindex="-1" class="typeahead-hint" style="border-color: transparent; position: absolute; top: 0px; display: inline; z-index: -1; float: none; color: rgb(192, 192, 192); box-shadow: none; cursor: default; user-select: none;"></span><span class="typeahead-button"><button type="submit"><span class="typeahead-search-icon"></span></button></span></div><div class="typeahead-result"><ul class="typeahead-list"><li class="typeahead-group" data-search-group="jupyter-notebook"><a href="javascript:;">jupyter-notebook command group</a></li><li class="active"><a href="javascript:;" data-group="jupyter-notebook" data-index="0"><i class="fa fa-icon {{icon}}"></i><strong>change cell to heading 5</strong>  <div title="jupyter-notebook:change-cell-to-heading-5" class="pull-right command-shortcut"><kbd>5</kbd></div></a></li></ul></div></div></form></div></div></div></div><div class="modal cmd-palette" style="display: none;"><div class="modal-dialog"><div class="modal-content"><div class="modal-body"><form><div class="typeahead-container"><div class="typeahead-field"><span class="typeahead-query" style="position: relative;"><input type="search"><input type="search" readonly="readonly" unselectable="on" tabindex="-1" class="typeahead-hint" style="border-color: transparent; position: absolute; top: 0px; display: inline; z-index: -1; float: none; color: rgb(192, 192, 192); box-shadow: none; cursor: default; user-select: none;"></span><span class="typeahead-button"><button type="submit"><span class="typeahead-search-icon"></span></button></span></div><div class="typeahead-result"><ul class="typeahead-list"><li class="typeahead-group" data-search-group="jupyter-notebook"><a href="javascript:;">jupyter-notebook command group</a></li><li class="active"><a href="javascript:;" data-group="jupyter-notebook" data-index="0"><i class="fa fa-icon {{icon}}"></i><strong>change cell to heading 5</strong>  <div title="jupyter-notebook:change-cell-to-heading-5" class="pull-right command-shortcut"><kbd>5</kbd></div></a></li></ul></div></div></form></div></div></div></div><div class="modal cmd-palette" style="display: none;"><div class="modal-dialog"><div class="modal-content"><div class="modal-body"><form><div class="typeahead-container"><div class="typeahead-field"><span class="typeahead-query" style="position: relative;"><input type="search"><input type="search" readonly="readonly" unselectable="on" tabindex="-1" class="typeahead-hint" style="border-color: transparent; position: absolute; top: 0px; display: inline; z-index: -1; float: none; color: rgb(192, 192, 192); box-shadow: none; cursor: default; user-select: none;"></span><span class="typeahead-button"><button type="submit"><span class="typeahead-search-icon"></span></button></span></div><div class="typeahead-result"><ul class="typeahead-list"><li class="typeahead-group" data-search-group="jupyter-notebook"><a href="javascript:;">jupyter-notebook command group</a></li><li class="active"><a href="javascript:;" data-group="jupyter-notebook" data-index="0"><i class="fa fa-icon {{icon}}"></i><strong>change cell to heading 5</strong>  <div title="jupyter-notebook:change-cell-to-heading-5" class="pull-right command-shortcut"><kbd>5</kbd></div></a></li></ul></div></div></form></div></div></div></div><div class="modal cmd-palette" style="display: none;"><div class="modal-dialog"><div class="modal-content"><div class="modal-body"><form><div class="typeahead-container"><div class="typeahead-field"><span class="typeahead-query" style="position: relative;"><input type="search"><input type="search" readonly="readonly" unselectable="on" tabindex="-1" class="typeahead-hint" style="border-color: transparent; position: absolute; top: 0px; display: inline; z-index: -1; float: none; color: rgb(192, 192, 192); box-shadow: none; cursor: default; user-select: none;"></span><span class="typeahead-button"><button type="submit"><span class="typeahead-search-icon"></span></button></span></div><div class="typeahead-result"><ul class="typeahead-list"><li class="typeahead-group" data-search-group="jupyter-notebook"><a href="javascript:;">jupyter-notebook command group</a></li><li class="active"><a href="javascript:;" data-group="jupyter-notebook" data-index="0"><i class="fa fa-icon {{icon}}"></i><strong>change cell to heading 5</strong>  <div title="jupyter-notebook:change-cell-to-heading-5" class="pull-right command-shortcut"><kbd>5</kbd></div></a></li></ul></div></div></form></div></div></div></div><div class="modal cmd-palette" style="display: none;"><div class="modal-dialog"><div class="modal-content"><div class="modal-body"><form><div class="typeahead-container"><div class="typeahead-field"><span class="typeahead-query" style="position: relative;"><input type="search"><input type="search" readonly="readonly" unselectable="on" tabindex="-1" class="typeahead-hint" style="border-color: transparent; position: absolute; top: 0px; display: inline; z-index: -1; float: none; color: rgb(192, 192, 192); box-shadow: none; cursor: default; user-select: none;"></span><span class="typeahead-button"><button type="submit"><span class="typeahead-search-icon"></span></button></span></div><div class="typeahead-result"><ul class="typeahead-list"><li class="typeahead-group" data-search-group="jupyter-notebook"><a href="javascript:;">jupyter-notebook command group</a></li><li class="active"><a href="javascript:;" data-group="jupyter-notebook" data-index="0"><i class="fa fa-icon {{icon}}"></i><strong>change cell to heading 5</strong>  <div title="jupyter-notebook:change-cell-to-heading-5" class="pull-right command-shortcut"><kbd>5</kbd></div></a></li></ul></div></div></form></div></div></div></div><div class="modal cmd-palette" style="display: none;"><div class="modal-dialog"><div class="modal-content"><div class="modal-body"><form><div class="typeahead-container"><div class="typeahead-field"><span class="typeahead-query" style="position: relative;"><input type="search"><input type="search" readonly="readonly" unselectable="on" tabindex="-1" class="typeahead-hint" style="border-color: transparent; position: absolute; top: 0px; display: inline; z-index: -1; float: none; color: rgb(192, 192, 192); box-shadow: none; cursor: default; user-select: none;"></span><span class="typeahead-button"><button type="submit"><span class="typeahead-search-icon"></span></button></span></div><div class="typeahead-result"><ul class="typeahead-list"><li class="typeahead-group" data-search-group="jupyter-notebook"><a href="javascript:;">jupyter-notebook command group</a></li><li class="active"><a href="javascript:;" data-group="jupyter-notebook" data-index="0"><i class="fa fa-icon {{icon}}"></i><strong>change cell to heading 5</strong>  <div title="jupyter-notebook:change-cell-to-heading-5" class="pull-right command-shortcut"><kbd>5</kbd></div></a></li></ul></div></div></form></div></div></div></div><div class="modal cmd-palette" style="display: none;"><div class="modal-dialog"><div class="modal-content"><div class="modal-body"><form><div class="typeahead-container"><div class="typeahead-field"><span class="typeahead-query" style="position: relative;"><input type="search"><input type="search" readonly="readonly" unselectable="on" tabindex="-1" class="typeahead-hint" style="border-color: transparent; position: absolute; top: 0px; display: inline; z-index: -1; float: none; color: rgb(192, 192, 192); box-shadow: none; cursor: default; user-select: none;"></span><span class="typeahead-button"><button type="submit"><span class="typeahead-search-icon"></span></button></span></div><div class="typeahead-result"><ul class="typeahead-list"><li class="typeahead-group" data-search-group="jupyter-notebook"><a href="javascript:;">jupyter-notebook command group</a></li><li class="active"><a href="javascript:;" data-group="jupyter-notebook" data-index="0"><i class="fa fa-icon {{icon}}"></i><strong>change cell to heading 5</strong>  <div title="jupyter-notebook:change-cell-to-heading-5" class="pull-right command-shortcut"><kbd>5</kbd></div></a></li></ul></div></div></form></div></div></div></div><div class="modal cmd-palette" style="display: none;"><div class="modal-dialog"><div class="modal-content"><div class="modal-body"><form><div class="typeahead-container"><div class="typeahead-field"><span class="typeahead-query" style="position: relative;"><input type="search"><input type="search" readonly="readonly" unselectable="on" tabindex="-1" class="typeahead-hint" style="border-color: transparent; position: absolute; top: 0px; display: inline; z-index: -1; float: none; color: rgb(192, 192, 192); box-shadow: none; cursor: default; user-select: none;"></span><span class="typeahead-button"><button type="submit"><span class="typeahead-search-icon"></span></button></span></div><div class="typeahead-result"><ul class="typeahead-list"><li class="typeahead-group" data-search-group="jupyter-notebook"><a href="javascript:;">jupyter-notebook command group</a></li><li class="active"><a href="javascript:;" data-group="jupyter-notebook" data-index="0"><i class="fa fa-icon {{icon}}"></i><strong>change cell to heading 5</strong>  <div title="jupyter-notebook:change-cell-to-heading-5" class="pull-right command-shortcut"><kbd>5</kbd></div></a></li></ul></div></div></form></div></div></div></div><div class="modal cmd-palette" style="display: none;"><div class="modal-dialog"><div class="modal-content"><div class="modal-body"><form><div class="typeahead-container"><div class="typeahead-field"><span class="typeahead-query" style="position: relative;"><input type="search"><input type="search" readonly="readonly" unselectable="on" tabindex="-1" class="typeahead-hint" style="border-color: transparent; position: absolute; top: 0px; display: inline; z-index: -1; float: none; color: rgb(192, 192, 192); box-shadow: none; cursor: default; user-select: none;"></span><span class="typeahead-button"><button type="submit"><span class="typeahead-search-icon"></span></button></span></div><div class="typeahead-result"><ul class="typeahead-list"><li class="typeahead-group" data-search-group="jupyter-notebook"><a href="javascript:;">jupyter-notebook command group</a></li><li class="active"><a href="javascript:;" data-group="jupyter-notebook" data-index="0"><i class="fa fa-icon {{icon}}"></i><strong>change cell to heading 5</strong>  <div title="jupyter-notebook:change-cell-to-heading-5" class="pull-right command-shortcut"><kbd>5</kbd></div></a></li></ul></div></div></form></div></div></div></div></body></html>