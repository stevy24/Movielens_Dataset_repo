<!DOCTYPE html>
<!-- saved from url=(0103)http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb -->
<html lang="fr-fr"><head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    

    <title>RSs_Python</title>
    
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
<link rel="stylesheet" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb" id="kernel-css" type="text/css">


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

    
    

<script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="services/contents" src="./README_files/contents.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="custom/custom" src="./README_files/custom.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/plotlywidget/extension" src="./README_files/extension.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/jupyter-js-widgets/extension" src="./README_files/extension.js(1).download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/nbextensions_configurator/config_menu/main" src="./README_files/main.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/contrib_nbextensions_help_item/main" src="./README_files/main.js(1).download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/varInspector/main" src="./README_files/main.js(2).download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/code_prettify/code_prettify" src="./README_files/code_prettify.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/collapsible_headings/main" src="./README_files/main.js(3).download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/toc2/main" src="./README_files/main.js(4).download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/codefolding/main" src="./README_files/main.js(5).download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/export_embedded/main" src="./README_files/main.js(6).download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/code_prettify/autopep8" src="./README_files/autopep8.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/code_font_size/code_font_size" src="./README_files/code_font_size.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/gist_it/main" src="./README_files/main.js(7).download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/python-markdown/main" src="./README_files/main.js(8).download"></script><style type="text/css">.MathJax_Hover_Frame {border-radius: .25em; -webkit-border-radius: .25em; -moz-border-radius: .25em; -khtml-border-radius: .25em; box-shadow: 0px 0px 15px #83A; -webkit-box-shadow: 0px 0px 15px #83A; -moz-box-shadow: 0px 0px 15px #83A; -khtml-box-shadow: 0px 0px 15px #83A; border: 1px solid #A6D ! important; display: inline-block; position: absolute}
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
</style><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/code_prettify/kernel_exec_on_cell" src="./README_files/kernel_exec_on_cell.js.download"></script><link type="text/css" rel="stylesheet" href="./README_files/main.css"><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/toc2/toc2" src="./README_files/toc2.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="codemirror/addon/fold/foldcode" src="./README_files/foldcode.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="codemirror/addon/fold/foldgutter" src="./README_files/foldgutter.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="codemirror/addon/fold/brace-fold" src="./README_files/brace-fold.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="codemirror/addon/fold/indent-fold" src="./README_files/indent-fold.js.download"></script><link id="collapsible_headings_css" rel="stylesheet" type="text/css" href="./README_files/main(1).css"><link type="text/css" rel="stylesheet" href="./README_files/main(2).css"><style id="collapsible_headings_indent_css">.collapsible_headings_toggle .h1 { margin-right: 40px; }
.collapsible_headings_toggle .h2 { margin-right: 32px; }
.collapsible_headings_toggle .h3 { margin-right: 24px; }
.collapsible_headings_toggle .h4 { margin-right: 16px; }
.collapsible_headings_toggle .h5 { margin-right: 8px; }
.collapsible_headings_toggle .h6 { margin-right: 0px; }</style><style type="text/css">div.MathJax_MathML {text-align: center; margin: .75em 0px; display: block!important}
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
</style><link type="text/css" rel="stylesheet" href="./README_files/main(3).css"><link type="text/css" rel="stylesheet" href="./README_files/foldgutter.css"><link type="text/css" rel="stylesheet" href="./README_files/foldgutter(1).css"><style type="text/css">.MathJax_Display {text-align: center; margin: 0; position: relative; display: block!important; text-indent: 0; max-width: none; max-height: none; min-width: 0; min-height: 0; width: 100%}
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
</style><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/codefolding/firstline-fold" src="./README_files/firstline-fold.js.download"></script><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/codefolding/magic-fold" src="./README_files/magic-fold.js.download"></script><style type="text/css">/*
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
</style><link id="favicon" type="image/x-icon" rel="shortcut icon" href="http://localhost:8888/static/base/images/favicon-notebook.ico"><script type="text/javascript" charset="utf-8" async="" data-requirecontext="_" data-requiremodule="nbextensions/varInspector/jquery.tablesorter.min" src="./README_files/jquery.tablesorter.min.js.download"></script></head>

<body class="notebook_app command_mode" data-jupyter-api-token="52c38a14dd2558403e4ca62e1a12ae0445fb373538fc29b9" data-base-url="/" data-ws-url="" data-notebook-name="RSs_Python.ipynb" data-notebook-path="Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb" dir="ltr" style=""><div style="visibility: hidden; overflow: hidden; position: absolute; top: 0px; height: 1px; width: auto; padding: 0px; border: 0px; margin: 0px; text-align: left; text-indent: 0px; text-transform: none; line-height: normal; letter-spacing: normal; word-spacing: normal;"><div id="MathJax_Hidden"></div></div><div id="MathJax_Message" style="display: none;"></div>

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
    <span id="notebook_name" class="filename">RSs_Python</span>
    <span class="checkpoint_status" title="lun. 4 mars 2019 09:34">Last Checkpoint: Hier à 09:34</span>
    <span class="autosave_status">(autosaved)</span>
<i id="notebook-trusted-indicator" class="fa fa-question notebook-trusted" title="Notebook is not trusted"></i></span>

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
            <span id="notification_area"><div id="notification_kernel" class="notification_widget btn btn-xs navbar-btn undefined info" style="display: none;"><span></span></div><div id="notification_notebook" class="notification_widget btn btn-xs navbar-btn" style="display: none;"><span></span></div><div id="notification_trusted" class="notification_widget btn btn-xs navbar-btn" style=""><span title="Javascript disabled for notebook display">Not Trusted</span></div><div id="notification_widgets" class="notification_widget btn btn-xs navbar-btn" style="display: none;"><span></span></div></span>
            <div class="navbar-collapse collapse">
              <ul class="nav navbar-nav">
                <li class="dropdown"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#" class="dropdown-toggle" data-toggle="dropdown">File</a>
                    <ul id="file_menu" class="dropdown-menu">
                        <li id="new_notebook" class="dropdown-submenu">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">New Notebook</a>
                            <ul class="dropdown-menu" id="menu-new-notebook-submenu"><li id="new-notebook-submenu-python3"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Python 3</a></li></ul>
                        </li>
                        <li id="open_notebook" title="Opens a new window with the Dashboard view">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Open...</a></li>
                        <!-- <hr/> -->
                        <li class="divider"></li>
                        <li id="copy_notebook" title="Open a copy of this notebook&#39;s contents and start a new kernel">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Make a Copy...</a></li>
                        <li id="save_notebook_as" title="Save a copy of the notebook&#39;s contents and start a new kernel">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Save as...</a></li>
                        <li id="rename_notebook"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Rename...</a></li>
                        <li id="save_checkpoint"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Save and Checkpoint</a></li>
                        <!-- <hr/> -->
                        <li class="divider"></li>
                        <li id="restore_checkpoint" class="dropdown-submenu"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Revert to Checkpoint</a>
                          <ul class="dropdown-menu"><li><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">lundi 4 mars 2019 09:34</a></li></ul>
                        </li>
                        <li class="divider"></li>
                        <li id="print_preview"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Print Preview</a></li>
                        <li class="dropdown-submenu"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Download as</a>
                            <ul id="download_menu" class="dropdown-menu">
                                <li id="download_ipynb"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Notebook (.ipynb)</a></li>
                                <li id="download_script"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Python (.py)</a></li>
                                <li id="download_html"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">HTML (.html)</a></li>
                                <li id="download_slides"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Reveal.js slides (.html)</a></li>
                                <li id="download_markdown"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Markdown (.md)</a></li>
                                <li id="download_rst"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">reST (.rst)</a></li>
                                <li id="download_latex"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">LaTeX (.tex)</a></li>
                                <li id="download_pdf"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">PDF via LaTeX (.pdf)</a></li>
                                
                                <li id="download_asciidoc">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">asciidoc (.asciidoc)</a>
                                </li>
                                
                                <li id="download_custom">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">custom (.txt)</a>
                                </li>
                                
                                <li id="download_html">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">custom (.html)</a>
                                </li>
                                
                                <li id="download_html_ch">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">custom (.html)</a>
                                </li>
                                
                                <li id="download_html_embed">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">custom (.html)</a>
                                </li>
                                
                                <li id="download_html_toc">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">custom (.html)</a>
                                </li>
                                
                                <li id="download_html_with_lenvs">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">custom (.html)</a>
                                </li>
                                
                                <li id="download_html_with_toclenvs">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">custom (.html)</a>
                                </li>
                                
                                <li id="download_latex">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">latex (.tex)</a>
                                </li>
                                
                                <li id="download_latex_with_lenvs">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">latex (.tex)</a>
                                </li>
                                
                                <li id="download_markdown">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">markdown (.md)</a>
                                </li>
                                
                                <li id="download_notebook">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">notebook (.ipynb)</a>
                                </li>
                                
                                <li id="download_pdf">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">pdf (.tex)</a>
                                </li>
                                
                                <li id="download_python">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">python (.py)</a>
                                </li>
                                
                                <li id="download_rst">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">rst (.rst)</a>
                                </li>
                                
                                <li id="download_script">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">custom (.txt)</a>
                                </li>
                                
                                <li id="download_selectLanguage">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">notebook (.ipynb)</a>
                                </li>
                                
                                <li id="download_slides">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">slides (.slides.html)</a>
                                </li>
                                
                                <li id="download_slides_with_lenvs">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">slides (.slides.html)</a>
                                </li>
                                
                            <li id="download_html_embed"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">HTML Embedded (.html)</a></li></ul>
                        </li>
                        <li class="dropdown-submenu hidden"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Deploy as</a>
                            <ul id="deploy_menu" class="dropdown-menu"></ul>
                        </li>
                        <li class="divider"></li>
                        <li id="trust_notebook" title="Trust the output of this notebook">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Trust Notebook</a></li>
                        <li class="divider"></li>
                        <li id="close_and_halt" title="Shutdown this notebook&#39;s kernel, and close this window">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Close and Halt</a></li>
                    </ul>
                </li>
                <li class="dropdown"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#" class="dropdown-toggle" data-toggle="dropdown">Edit</a>
                    <ul id="edit_menu" class="dropdown-menu">
                        <li id="cut_cell"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Cut Cells</a></li>
                        <li id="copy_cell"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Copy Cells</a></li>
                        <li id="paste_cell_above" class="disabled"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Paste Cells Above</a></li>
                        <li id="paste_cell_below" class="disabled"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Paste Cells Below</a></li>
                        <li id="paste_cell_replace" class="disabled"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Paste Cells &amp; Replace</a></li>
                        <li id="delete_cell"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Delete Cells</a></li>
                        <li id="undelete_cell" class="disabled"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Undo Delete Cells</a></li>
                        <li class="divider"></li>
                        <li id="split_cell"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Split Cell</a></li>
                        <li id="merge_cell_above"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Merge Cell Above</a></li>
                        <li id="merge_cell_below"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Merge Cell Below</a></li>
                        <li class="divider"></li>
                        <li id="move_cell_up"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Move Cell Up</a></li>
                        <li id="move_cell_down"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Move Cell Down</a></li>
                        <li class="divider"></li>
                        <li id="edit_nb_metadata"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Edit Notebook Metadata</a></li>
                        <li class="divider"></li>
                        <li id="find_and_replace"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#"> Find and Replace </a></li>
                        <li class="divider"></li>
                        <li id="cut_cell_attachments"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Cut Cell Attachments</a></li>
                        <li id="copy_cell_attachments"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Copy Cell Attachments</a></li>
                        <li id="paste_cell_attachments" class="disabled"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Paste Cell Attachments</a></li>
                        <li class="divider"></li>
                        <li id="insert_image" class="disabled"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#"> Insert Image </a></li>
                    <li class="divider"></li><li><a target="_blank" title="Opens in a new window" href="http://localhost:8888/nbextensions/"> <i class="fa fa-cogs menu-icon pull-right"></i><span>nbextensions config</span></a></li></ul>
                </li>
                <li class="dropdown"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#" class="dropdown-toggle" data-toggle="dropdown">View</a>
                    <ul id="view_menu" class="dropdown-menu">
                        <li id="toggle_header" title="Show/Hide the logo and notebook title (above menu bar)">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Toggle Header</a>
                        </li>
                        <li id="toggle_toolbar" title="Show/Hide the action icons (below menu bar)">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Toggle Toolbar</a>
                        </li>
                        <li id="toggle_line_numbers" title="Show/Hide line numbers in cells">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Toggle Line Numbers</a>
                        </li>
                        <li id="menu-cell-toolbar" class="dropdown-submenu">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Cell Toolbar</a>
                            <ul class="dropdown-menu" id="menu-cell-toolbar-submenu"><li data-name="None"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">None</a></li><li data-name="Edit%20Metadata"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Edit Metadata</a></li><li data-name="Raw%20Cell%20Format"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Raw Cell Format</a></li><li data-name="Slideshow"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Slideshow</a></li><li data-name="Attachments"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Attachments</a></li><li data-name="Tags"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Tags</a></li></ul>
                        </li>
                    </ul>
                </li>
                <li class="dropdown"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#" class="dropdown-toggle" data-toggle="dropdown">Insert</a>
                    <ul id="insert_menu" class="dropdown-menu">
                        <li id="insert_cell_above" title="Insert an empty Code cell above the currently active cell">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Insert Cell Above</a></li>
                        <li id="insert_cell_below" title="Insert an empty Code cell below the currently active cell">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Insert Cell Below</a></li>
                    <li class="divider"></li><li><a title="Insert a heading cell above the selected cell" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Insert Heading Above</a></li><li><a title="Insert a heading cell below the selected cell&#39;s section" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Insert Heading Below</a></li></ul>
                </li>
                <li class="dropdown"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#" class="dropdown-toggle" data-toggle="dropdown">Cell</a>
                    <ul id="cell_menu" class="dropdown-menu">
                        <li id="run_cell" title="Run this cell, and move cursor to the next one">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Run Cells</a></li>
                        <li id="run_cell_select_below" title="Run this cell, select below">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Run Cells and Select Below</a></li>
                        <li id="run_cell_insert_below" title="Run this cell, insert below">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Run Cells and Insert Below</a></li>
                        <li id="run_all_cells" title="Run all cells in the notebook">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Run All</a></li>
                        <li id="run_all_cells_above" title="Run all cells above (but not including) this cell">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Run All Above</a></li>
                        <li id="run_all_cells_below" title="Run this cell and all cells below it">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Run All Below</a></li>
                        <li class="divider"></li>
                        <li id="change_cell_type" class="dropdown-submenu" title="All cells in the notebook have a cell type. By default, new cells are created as &#39;Code&#39; cells">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Cell Type</a>
                            <ul class="dropdown-menu">
                              <li id="to_code" title="Contents will be sent to the kernel for execution, and output will display in the footer of cell">
                                  <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Code</a></li>
                              <li id="to_markdown" title="Contents will be rendered as HTML and serve as explanatory text">
                                  <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Markdown</a></li>
                              <li id="to_raw" title="Contents will pass through nbconvert unmodified">
                                  <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Raw NBConvert</a></li>
                            </ul>
                        </li>
                        <li class="divider"></li>
                        <li id="current_outputs" class="dropdown-submenu"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Current Outputs</a>
                            <ul class="dropdown-menu">
                                <li id="toggle_current_output" title="Hide/Show the output of the current cell">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Toggle</a>
                                </li>
                                <li id="toggle_current_output_scroll" title="Scroll the output of the current cell">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Toggle Scrolling</a>
                                </li>
                                <li id="clear_current_output" title="Clear the output of the current cell">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Clear</a>
                                </li>
                            </ul>
                        </li>
                        <li id="all_outputs" class="dropdown-submenu"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">All Output</a>
                            <ul class="dropdown-menu">
                                <li id="toggle_all_output" title="Hide/Show the output of all cells">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Toggle</a>
                                </li>
                                <li id="toggle_all_output_scroll" title="Scroll the output of all cells">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Toggle Scrolling</a>
                                </li>
                                <li id="clear_all_output" title="Clear the output of all cells">
                                    <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Clear</a>
                                </li>
                            </ul>
                        </li>
                    </ul>
                </li>
                <li class="dropdown"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#" class="dropdown-toggle" data-toggle="dropdown">Kernel</a>
                    <ul id="kernel_menu" class="dropdown-menu">
                        <li id="int_kernel" title="Send Keyboard Interrupt (CTRL-C) to the Kernel">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Interrupt</a>
                        </li>
                        <li id="restart_kernel" title="Restart the Kernel">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Restart</a>
                        </li>
                        <li id="restart_clear_output" title="Restart the Kernel and clear all output">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Restart &amp; Clear Output</a>
                        </li>
                        <li id="restart_run_all" title="Restart the Kernel and re-run the notebook">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Restart &amp; Run All</a>
                        </li>
                        <li id="reconnect_kernel" title="Reconnect to the Kernel">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Reconnect</a>
                        </li>
                        <li id="shutdown_kernel" title="Shutdown the Kernel">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Shutdown</a>
                        </li>
                        <li class="divider"></li>
                        <li id="menu-change-kernel" class="dropdown-submenu">
                            <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Change kernel</a>
                            <ul class="dropdown-menu" id="menu-change-kernel-submenu"><li id="kernel-submenu-python3"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Python 3</a></li></ul>
                        </li>
                    </ul>
                </li><li id="Navigate" class="dropdown"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#" id="Navigate_sub" class="dropdown-toggle" data-toggle="dropdown">Navigate</a><ul id="Navigate_menu" class="dropdown-menu ui-resizable" style=""><div id="navigate_menu" class="toc" style="width: 160px; height: 0px;"><ul class="toc-item"><li><span><i class="fa fa-fw fa-caret-down"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#Recommender-Systems-with-Python" data-toc-modified-id="Recommender-Systems-with-Python-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>Recommender Systems with Python</a></span><ul class="toc-item"><li><span><i class="fa fa-fw"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#(Optional-and-additional-topic-in-the-course)" data-toc-modified-id="(Optional-and-additional-topic-in-the-course)-1.1"><span class="toc-item-num">1.1&nbsp;&nbsp;</span>(Optional and additional topic in the course)</a></span></li><li><span><i class="fa fa-fw"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#Let&#39;s-do-some-pre-processing-on-the-data-now!" data-toc-modified-id="Let&#39;s-do-some-pre-processing-on-the-data-now!-1.2"><span class="toc-item-num">1.2&nbsp;&nbsp;</span>Let's do some pre-processing on the data now!</a></span></li><li><span><i class="fa fa-fw"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#EDA" data-toc-modified-id="EDA-1.3" class=""><span class="toc-item-num">1.3&nbsp;&nbsp;</span>EDA</a></span></li><li><span><i class="fa fa-fw"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#Recommender-System-for-similar-movie" data-toc-modified-id="Recommender-System-for-similar-movie-1.4" class="toc-item-highlight-select"><span class="toc-item-num">1.4&nbsp;&nbsp;</span>Recommender System for similar movie</a></span></li><li><span><i class="fa fa-fw"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#Excellent-work!" data-toc-modified-id="Excellent-work!-1.5"><span class="toc-item-num">1.5&nbsp;&nbsp;</span>Excellent work!</a></span></li><li><span><i class="fa fa-fw"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#Interested-to-learn-and-play-with-more-dataset-to-develop-you-own-Recommender-Systems-?" data-toc-modified-id="Interested-to-learn-and-play-with-more-dataset-to-develop-you-own-Recommender-Systems-?-1.6"><span class="toc-item-num">1.6&nbsp;&nbsp;</span>Interested to learn and play with more dataset to develop you own Recommender Systems ?</a></span></li><li><span><i class="fa fa-fw"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#Good-Luck!" data-toc-modified-id="Good-Luck!-1.7"><span class="toc-item-num">1.7&nbsp;&nbsp;</span>Good Luck!</a></span></li></ul></li></ul></div><div class="ui-resizable-handle ui-resizable-e" style="z-index: 90;"></div><div class="ui-resizable-handle ui-resizable-s" style="z-index: 90;"></div><div class="ui-resizable-handle ui-resizable-se ui-icon ui-icon-gripsmall-diagonal-se" style="z-index: 90;"></div></ul></li>
                <li class="dropdown"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#" data-toggle="dropdown" class="dropdown-toggle">Widgets</a><ul id="widget-submenu" class="dropdown-menu"><li title="Save the notebook with the widget state information for static rendering"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Save Notebook Widget State</a></li><li title="Clear the widget state information from the notebook"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Clear Notebook Widget State</a></li><ul class="divider"></ul><li title="Download the widget state as a JSON file"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Download Widget State</a></li><li title="Embed interactive widgets"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Embed Widgets</a></li></ul></li><li class="dropdown"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#" class="dropdown-toggle" data-toggle="dropdown">Help</a>
                    <ul id="help_menu" class="dropdown-menu">
                        
                        <li id="notebook_tour" title="A quick tour of the notebook user interface"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">User Interface Tour</a></li>
                        <li id="keyboard_shortcuts" title="Opens a tooltip with all keyboard shortcuts"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Keyboard Shortcuts</a></li>
                        <li id="edit_keyboard_shortcuts" title="Opens a dialog allowing you to edit Keyboard shortcuts"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">Edit Keyboard Shortcuts</a></li>
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
                        <li title="About Jupyter Notebook"><a id="notebook_about" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#">About</a></li>
                        
                    </ul>
                </li>
              </ul>
            </div>
        </div>
    </div>
</div>

<div id="maintoolbar" class="navbar">
  <div class="toolbar-inner navbar-inner navbar-nobg">
    <div id="maintoolbar-container" class="container toolbar"><div class="btn-group" id="save-notbook"><button class="btn btn-default" title="Save and Checkpoint" data-jupyter-action="jupyter-notebook:save-notebook"><i class="fa-save fa"></i></button></div><div class="btn-group" id="insert_above_below"><button class="btn btn-default" title="insert cell below" data-jupyter-action="jupyter-notebook:insert-cell-below"><i class="fa-plus fa"></i></button></div><div class="btn-group" id="cut_copy_paste"><button class="btn btn-default" title="cut selected cells" data-jupyter-action="jupyter-notebook:cut-cell"><i class="fa-cut fa"></i></button><button class="btn btn-default" title="copy selected cells" data-jupyter-action="jupyter-notebook:copy-cell"><i class="fa-copy fa"></i></button><button class="btn btn-default" title="paste cells below" data-jupyter-action="jupyter-notebook:paste-cell-below"><i class="fa-paste fa"></i></button></div><div class="btn-group" id="move_up_down"><button class="btn btn-default" title="move selected cells up" data-jupyter-action="jupyter-notebook:move-cell-up"><i class="fa-arrow-up fa"></i></button><button class="btn btn-default" title="move selected cells down" data-jupyter-action="jupyter-notebook:move-cell-down"><i class="fa-arrow-down fa"></i></button></div><div class="btn-group" id="run_int"><button class="btn btn-default" title="Run" data-jupyter-action="jupyter-notebook:run-cell-and-select-next"><i class="fa-step-forward fa"></i><span class="toolbar-btn-label">Run</span></button><button class="btn btn-default" title="interrupt the kernel" data-jupyter-action="jupyter-notebook:interrupt-kernel"><i class="fa-stop fa"></i></button><button class="btn btn-default" title="restart the kernel (with dialog)" data-jupyter-action="jupyter-notebook:confirm-restart-kernel"><i class="fa-repeat fa"></i></button><button class="btn btn-default" title="restart the kernel, then re-run the whole notebook (with dialog)" data-jupyter-action="jupyter-notebook:confirm-restart-kernel-and-run-all-cells"><i class="fa-forward fa"></i></button></div><select id="cell_type" class="form-control select-xs"><option value="code">Code</option><option value="markdown">Markdown</option><option value="raw">Raw NBConvert</option><option value="heading">Heading</option><option value="multiselect" disabled="disabled" style="display: none;">-</option></select><div class="btn-group"><button class="btn btn-default" title="open the command palette" data-jupyter-action="jupyter-notebook:show-command-palette"><i class="fa-keyboard-o fa"></i></button></div><div class="btn-group"><button class="btn btn-default" title="Variable Inspector" data-jupyter-action="varInspector:toggle-variable-inspector" id="varInspector_button"><i class="fa-crosshairs fa"></i></button></div><div class="btn-group"><button class="btn btn-default" title="Create/Edit Gist of Notebook" data-jupyter-action="gist_it:create-gist-from-notebook"><i class="fa-github fa"></i></button></div><div class="btn-group"><button class="btn btn-default" title="Increase code font size" data-jupyter-action="code_font_size:increase-code-font-size"><i class="fa-search-plus fa"></i></button><button class="btn btn-default" title="Decrease code font size" data-jupyter-action="code_font_size:decrease-code-font-size"><i class="fa-search-minus fa"></i></button></div><div class="btn-group" id="code_prettify_button"><button class="btn btn-default" title="code_prettify selected cell(s) (add shift for all cells)"><i class="fa-legal fa"></i></button></div><div class="btn-group" id="autopep8_button"><button class="btn btn-default" title="autopep8 selected cell(s) (add shift for all cells)"><i class="fa-legal fa"></i></button></div><div class="btn-group"><button class="btn btn-default" title="Table of Contents" data-jupyter-action="toc2:toggle-toc" id="toc_button"><i class="fa-list fa"></i></button></div></div>
  </div>
</div>
</div>

<div class="lower-header-bar"></div>

</div>

<div id="site" style="display: block; height: 499px;"><div id="toc-wrapper" style="display: none; position: relative; width: 20%; top: 109.778px; left: 0px;" class="ui-draggable ui-resizable sidebar-wrapper"><div id="toc-header"><span class="header">Contents </span><i class="fa fa-fw hide-btn" title="Hide ToC"></i><i class="fa fa-fw fa-refresh" title="Reload ToC"></i><i class="fa fa-fw fa-cog" title="ToC settings"></i></div><div id="toc" class="toc"><ul class="toc-item"><li><span class=""><i class="fa fa-fw fa-caret-down"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#Recommender-Systems-with-Python" data-toc-modified-id="Recommender-Systems-with-Python-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>Recommender Systems with Python</a></span><ul class="toc-item"><li><span class=""><i class="fa fa-fw"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#(Optional-and-additional-topic-in-the-course)" data-toc-modified-id="(Optional-and-additional-topic-in-the-course)-1.1"><span class="toc-item-num">1.1&nbsp;&nbsp;</span>(Optional and additional topic in the course)</a></span></li><li><span class=""><i class="fa fa-fw"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#Let&#39;s-do-some-pre-processing-on-the-data-now!" data-toc-modified-id="Let&#39;s-do-some-pre-processing-on-the-data-now!-1.2"><span class="toc-item-num">1.2&nbsp;&nbsp;</span>Let's do some pre-processing on the data now!</a></span></li><li><span class=""><i class="fa fa-fw"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#EDA" data-toc-modified-id="EDA-1.3" class=""><span class="toc-item-num">1.3&nbsp;&nbsp;</span>EDA</a></span></li><li><span class=""><i class="fa fa-fw"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#Recommender-System-for-similar-movie" data-toc-modified-id="Recommender-System-for-similar-movie-1.4" class="toc-item-highlight-select"><span class="toc-item-num">1.4&nbsp;&nbsp;</span>Recommender System for similar movie</a></span></li><li><span class="highlight_on_scroll"><i class="fa fa-fw"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#Excellent-work!" data-toc-modified-id="Excellent-work!-1.5"><span class="toc-item-num">1.5&nbsp;&nbsp;</span>Excellent work!</a></span></li><li><span class=""><i class="fa fa-fw"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#Interested-to-learn-and-play-with-more-dataset-to-develop-you-own-Recommender-Systems-?" data-toc-modified-id="Interested-to-learn-and-play-with-more-dataset-to-develop-you-own-Recommender-Systems-?-1.6"><span class="toc-item-num">1.6&nbsp;&nbsp;</span>Interested to learn and play with more dataset to develop you own Recommender Systems ?</a></span></li><li><span class=""><i class="fa fa-fw"></i><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#Good-Luck!" data-toc-modified-id="Good-Luck!-1.7"><span class="toc-item-num">1.7&nbsp;&nbsp;</span>Good Luck!</a></span></li></ul></li></ul></div><div class="ui-resizable-handle ui-resizable-n" style="z-index: 90;"></div><div class="ui-resizable-handle ui-resizable-e ui-icon ui-icon-grip-dotted-vertical" style="z-index: 90;"></div><div class="ui-resizable-handle ui-resizable-s" style="z-index: 90;"></div><div class="ui-resizable-handle ui-resizable-w" style="z-index: 90;"></div><div class="ui-resizable-handle ui-resizable-se ui-icon-gripsmall-diagonal-se" style="z-index: 90;"></div><div class="ui-resizable-handle ui-resizable-sw" style="z-index: 90;"></div><div class="ui-resizable-handle ui-resizable-ne" style="z-index: 90;"></div><div class="ui-resizable-handle ui-resizable-nw" style="z-index: 90;"></div></div>


<div id="ipython-main-app">
    <div id="notebook_panel">
        <div id="notebook" tabindex="-1"><div class="container" id="notebook-container"><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59721px; left: 39.5972px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 28px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.59723px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">a</span> <span class="cm-attribute">href</span>=<span class="cm-string">'</span><span class="cm-string cm-link">http://www.scienceacademy.ca</span><span class="cm-string">'</span><span class="cm-tag cm-bracket">&gt;</span> <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">img</span> <span class="cm-attribute">style</span>=<span class="cm-string">"float: left;height:70px"</span> <span class="cm-attribute">src</span>=<span class="cm-string">"Log_SA.jpeg"</span><span class="cm-tag cm-bracket">&gt;&lt;/</span><span class="cm-tag">a</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 40px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p><a href="http://www.scienceacademy.ca/" target="_blank"> <img style="float: left ; height: 70px" src="./README_files/Log_SA.jpeg"></a></p>
</div></div></div><div class="cell text_cell unselected rendered collapsible_headings_ellipsis" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h1"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59721px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 509px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>18</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 21.3333px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation" style=""><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-1"># Recommender Systems with Python</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-2">## (Optional and additional topic in the course)</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Hi Guys, <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">5</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Very warm welcome to the Recommender Systems with Python lecture!<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">6</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">7</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">In this section, we are going to develop and Recommendation System that will suggest an item to the user, based on the similarity of a particular item, according to his/her interests. Please note, this will be a very basic Recommendation System to suggest similar items. <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">8</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">9</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">&amp;#9989; I want to mention that the skill-set in Recommendation Systems could lead you to a very rewarding career that you can built on this course. Once again, this is an optional topic in this course, however, based on the demand, I may put a complete course on developing true robust recommendation system in the near future. At this stage, the purpose of this topic is to make you realize that the knowledge you are getting from this course is unique, and can take you in variety of rewarding and in demand careers!<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">10</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">11</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Regarding the project in this lecture, we will be working with movielens dataset. The dataset consist of two <span class="cm-comment">`.csv`</span> files, <span class="cm-comment">`movies.csv`</span> and <span class="cm-comment">`ratings.csv`</span>. If you want, you can directly downloaded these files from <span class="cm-link">[the provided link]</span><span class="cm-string cm-url">(https://grouplens.org/datasets/movielens/)</span>. However, for your convenience , both of the files are are provided as a part of this course. At the end of this notebook, links to few other datasets are also provided, you can explore them if you really get interested in the recommender systems! <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">12</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">13</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-strong">**Good Luck**</span> <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">14</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">15</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-strong">**Let's start with some important imports!**</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">16</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">17</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">&amp;#9758; <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">font</span> <span class="cm-attribute">style</span>=<span class="cm-string">"font-size:12px;color:green;"</span><span class="cm-tag cm-bracket">&gt;</span> According to the grouplens.org:<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">18</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">*These datasets will change over time, and are not appropriate for reporting research results. We will keep the download links stable for automated downloads. We will not archive or make available previously released versions.*<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span> <span class="cm-tag cm-bracket">&lt;/</span><span class="cm-tag">font</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 509px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 521px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h1 id="Recommender-Systems-with-Python" data-toc-modified-id="Recommender-Systems-with-Python-1"><a class="toc-mod-link" id="Recommender-Systems-with-Python-1"></a><span class="toc-item-num">1&nbsp;&nbsp;</span>Recommender Systems with Python<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#Recommender-Systems-with-Python">¶</a></h1>
<h2 id="(Optional-and-additional-topic-in-the-course)" data-toc-modified-id="(Optional-and-additional-topic-in-the-course)-1.1"><a class="toc-mod-link" id="(Optional-and-additional-topic-in-the-course)-1.1"></a><span class="toc-item-num">1.1&nbsp;&nbsp;</span>(Optional and additional topic in the course)<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#(Optional-and-additional-topic-in-the-course)">¶</a></h2>
<p>Hi Guys, <br>
Very warm welcome to the Recommender Systems with Python lecture!<br></p>
<p>In this section, we are going to develop and Recommendation System that will suggest an item to the user, based on the similarity of a particular item, according to his/her interests. Please note, this will be a very basic Recommendation System to suggest similar items. <br></p>
<p>✅ I want to mention that the skill-set in Recommendation Systems could lead you to a very rewarding career that you can built on this course. Once again, this is an optional topic in this course, however, based on the demand, I may put a complete course on developing true robust recommendation system in the near future. At this stage, the purpose of this topic is to make you realize that the knowledge you are getting from this course is unique, and can take you in variety of rewarding and in demand careers!<br></p>
<p>Regarding the project in this lecture, we will be working with movielens dataset. The dataset consist of two <code>.csv</code> files, <code>movies.csv</code> and <code>ratings.csv</code>. If you want, you can directly downloaded these files from <a href="https://grouplens.org/datasets/movielens/" target="_blank">the provided link</a>. However, for your convenience , both of the files are are provided as a part of this course. At the end of this notebook, links to few other datasets are also provided, you can explore them if you really get interested in the recommender systems! <br></p>
<p><strong>Good Luck</strong> <br></p>
<p><strong>Let's start with some important imports!</strong></p>
<p>☞ <font style="font-size: 12px ; color: green"> According to the grouplens.org:<br>
<em>These datasets will change over time, and are not appropriate for reporting research results. We will keep the download links stable for automated downloads. We will not archive or make available previously released versions.</em><br> </font></p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[1]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.60059px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 154.819px; margin-bottom: -16px; border-right-width: 14px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-keyword">import</span> <span class="cm-variable">numpy</span> <span class="cm-keyword">as</span> <span class="cm-variable">np</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-keyword">import</span> <span class="cm-variable">pandas</span> <span class="cm-keyword">as</span> <span class="cm-variable">pd</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="height: 59px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output" style="display: none;"></div><div class="output" style="display: none;"></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59723px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 28px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We need to read the data files, let's read them first!</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 40px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>We need to read the data files, let's read them first!</p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[2]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59961px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 270.264px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">movies</span> <span class="cm-operator">=</span> <span class="cm-variable">pd</span>.<span class="cm-property">read_csv</span>(<span class="cm-string">'movies.csv'</span>)</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 42px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output" style="display: none;"></div><div class="output" style="display: none;"></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[3]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59961px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 285.653px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">ratings</span> <span class="cm-operator">=</span> <span class="cm-variable">pd</span>.<span class="cm-property">read_csv</span>(<span class="cm-string">'ratings.csv'</span>)</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 42px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output" style="display: none;"></div><div class="output" style="display: none;"></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59723px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 28px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">So, always good to check the head of the data!</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 40px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>So, always good to check the head of the data!</p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[4]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59961px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 123.889px; margin-bottom: -16px; border-right-width: 14px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">movies</span>.<span class="cm-property">head</span>()</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-comment">#ratings.head()</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="height: 59px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[4]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right">
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
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 28px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">So, in the movies dataset, we have movieId, the name or title of the movie and its category/genre!<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 40px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>So, in the movies dataset, we have movieId, the name or title of the movie and its category/genre!<br></p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[5]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59961px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 116.333px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">ratings</span>.<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 42px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[5]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right">
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
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 96px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>3</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.4445px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">In the ratings dataset, we have userId, movieId, rating that the movie got from a specific user, and the timestamp at which the movie got rating from the user. <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">If we look at both <span class="cm-comment">`ratings`</span> and <span class="cm-comment">`movies`</span> datasets, movieId column is a common column. Let's merge the dataframes on movieId and output the <span class="cm-comment">`head()`</span> of the merged data. </span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 96px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 108px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>In the ratings dataset, we have userId, movieId, rating that the movie got from a specific user, and the timestamp at which the movie got rating from the user. <br></p>
<p>If we look at both <code>ratings</code> and <code>movies</code> datasets, movieId column is a common column. Let's merge the dataframes on movieId and output the <code>head()</code> of the merged data. </p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[6]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59961px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 347.208px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">df</span> <span class="cm-operator">=</span> <span class="cm-variable">pd</span>.<span class="cm-property">merge</span>(<span class="cm-variable">ratings</span>, <span class="cm-variable">movies</span>, <span class="cm-variable">on</span><span class="cm-operator">=</span><span class="cm-string">'movieId'</span>)</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 42px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output" style="display: none;"></div><div class="output" style="display: none;"></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[7]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.60059px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 316.486px; margin-bottom: -16px; border-right-width: 14px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div><div class="CodeMirror-gutter-elt" style="left: 33px; width: 12px;"><div class="CodeMirror-foldgutter-open CodeMirror-guttermarker-subtle"></div></div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-comment"># let's check the head of our dataframe </span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">df</span>.<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="height: 59px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[7]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right">
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
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59729px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 45px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>2</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Now, we have a single dataframe with moveId and its tiles as two separate columns!<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">If you want, you can drop the genre column, we will not use this column in this project!<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 57px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>Now, we have a single dataframe with moveId and its tiles as two separate columns!<br>
If you want, you can drop the genre column, we will not use this column in this project!<br></p>
</div></div></div><div class="cell text_cell unselected rendered collapsible_headings_ellipsis" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h2"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59729px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 184px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>7</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 20.4444px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation" style=""><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-2">## Let's do some pre-processing on the data now!</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">The first thing we can do, we can create a dataframe that tells us average rating for the movie and number of ratings the movie got!<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">To do this, recall, the <span class="cm-comment">`groupby`</span> method, we can use this method here! <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">5</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">6</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">&amp;#9758; We need to <span class="cm-comment">`groupby`</span> the movies on <span class="cm-comment">`title`</span> and then grab the <span class="cm-comment">`rating`</span> column to get its mean, so that we have the mean rating of each movie. We can also use <span class="cm-comment">`sort_values(ascending = False)`</span> to re-arrange the entries from higher to lower mean rating and then check the head of dataframe, all in a single line code.<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">7</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Let do it!</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 184px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 196px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h2 id="Let&#39;s-do-some-pre-processing-on-the-data-now!" data-toc-modified-id="Let&#39;s-do-some-pre-processing-on-the-data-now!-1.2"><a class="toc-mod-link" id="Let&#39;s-do-some-pre-processing-on-the-data-now!-1.2"></a><span class="toc-item-num">1.2&nbsp;&nbsp;</span>Let's do some pre-processing on the data now!<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#Let&#39;s-do-some-pre-processing-on-the-data-now!">¶</a></h2>
<p>The first thing we can do, we can create a dataframe that tells us average rating for the movie and number of ratings the movie got!<br>
To do this, recall, the <code>groupby</code> method, we can use this method here! <br></p>
<p>☞ We need to <code>groupby</code> the movies on <code>title</code> and then grab the <code>rating</code> column to get its mean, so that we have the mean rating of each movie. We can also use <code>sort_values(ascending = False)</code> to re-arrange the entries from higher to lower mean rating and then check the head of dataframe, all in a single line code.<br>
Let do it!</p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[8]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.60059px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true" style="display: block; right: 0px; left: 46px;"><div style="height: 100%; min-height: 1px; width: 579px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 578.083px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 16px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">df</span>.<span class="cm-property">groupby</span>(<span class="cm-string">'title'</span>)[<span class="cm-string">'rating'</span>].<span class="cm-property">mean</span>().<span class="cm-property">sort_values</span>(<span class="cm-variable">ascending</span> <span class="cm-operator">=</span> <span class="cm-keyword">False</span>).<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 16px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 58px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[8]:</bdi></div><div class="output_subarea output_text output_result"><pre>title
Burn Up! (1991)                                     5.0
Absolute Giganten (1999)                            5.0
Gentlemen of Fortune (Dzhentlmeny udachi) (1972)    5.0
Erik the Viking (1989)                              5.0
Reality (2014)                                      5.0
Name: rating, dtype: float64</pre></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 197px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>9</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation" style=""><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">&amp;#9989; There is an important situation to consider in the above <span class="cm-comment">`groupby`</span> operation, while getting the <span class="cm-comment">`mean`</span> rating.<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable-2">* What if only 1 or 2 persons have watched a movie and gave a 5 stars rating to it! </span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable-2">* On the other hand, there could be a movie that got a good number of ratings between 1 and 5 stars. The average in such situation will be less then 5 but the number of watcher are higher!</span><span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">5</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">6</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Remember, this could be the case in our data, we may want to check the movies with number of ratings now.<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">7</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">8</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">&amp;#9758; Once again, <span class="cm-comment">`groupby`</span> on title and grab the <span class="cm-comment">`ratings`</span> column. Instead of <span class="cm-comment">`mean`</span>, we want <span class="cm-comment">`count`</span> for this task. We can again use <span class="cm-comment">`sort_values(ascending = False)`</span> to order the entries and check the head of our dataset.<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">9</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Let's do this!</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 197px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 209px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>✅ There is an important situation to consider in the above <code>groupby</code> operation, while getting the <code>mean</code> rating.<br></p>
<ul>
<li>What if only 1 or 2 persons have watched a movie and gave a 5 stars rating to it! </li>
<li>On the other hand, there could be a movie that got a good number of ratings between 1 and 5 stars. The average in such situation will be less then 5 but the number of watcher are higher!<br></li>
</ul>
<p>Remember, this could be the case in our data, we may want to check the movies with number of ratings now.<br></p>
<p>☞ Once again, <code>groupby</code> on title and grab the <code>ratings</code> column. Instead of <code>mean</code>, we want <code>count</code> for this task. We can again use <code>sort_values(ascending = False)</code> to order the entries and check the head of our dataset.<br>
Let's do this!</p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[9]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59961px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true" style="display: block; right: 0px; left: 46px;"><div style="height: 100%; min-height: 1px; width: 587px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 585.792px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 16px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">df</span>.<span class="cm-property">groupby</span>(<span class="cm-string">'title'</span>)[<span class="cm-string">'rating'</span>].<span class="cm-property">count</span>().<span class="cm-property">sort_values</span>(<span class="cm-variable">ascending</span> <span class="cm-operator">=</span> <span class="cm-keyword">False</span>).<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 16px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 58px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[9]:</bdi></div><div class="output_subarea output_text output_result"><pre>title
Forrest Gump (1994)                          341
Pulp Fiction (1994)                          324
Shawshank Redemption, The (1994)             311
Silence of the Lambs, The (1991)             304
Star Wars: Episode IV - A New Hope (1977)    291
Name: rating, dtype: int64</pre></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 147px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>5</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation" style=""><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">It looks like the top 5 famous movies don't have the 5 star average rating. <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">This is fine, you can imagine, if the movie, e.g. Forrest Gump got 341 ratings, all ratings must be 5 star to get average value of 5. <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Many of us may not know even the name of the movie with average 5 star rating, but, most of us might be familiar with the movies with most number of ratings, such as Start Wars in the list on number 5!<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">5</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Let's create a new dataframe <span class="cm-comment">`rating`</span>, in which we group the movies with their mean or average rating. Once again, we are going to use <span class="cm-comment">`groupby`</span> on title and grab the rating columns to get its mean. </span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 147px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 159px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>It looks like the top 5 famous movies don't have the 5 star average rating. <br>
This is fine, you can imagine, if the movie, e.g. Forrest Gump got 341 ratings, all ratings must be 5 star to get average value of 5. <br>
Many of us may not know even the name of the movie with average 5 star rating, but, most of us might be familiar with the movies with most number of ratings, such as Start Wars in the list on number 5!<br></p>
<p>Let's create a new dataframe <code>rating</code>, in which we group the movies with their mean or average rating. Once again, we are going to use <code>groupby</code> on title and grab the rating columns to get its mean. </p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[10]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 462.556px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">rating</span> <span class="cm-operator">=</span> <span class="cm-variable">pd</span>.<span class="cm-property">DataFrame</span>(<span class="cm-variable">df</span>.<span class="cm-property">groupby</span>(<span class="cm-string">'title'</span>)[<span class="cm-string">'rating'</span>].<span class="cm-property">mean</span>())</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 42px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output" style="display: none;"></div><div class="output" style="display: none;"></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[11]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 108.639px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">rating</span>.<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 42px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[11]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right">
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
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59741px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 113px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>3</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.4445px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">So, in the above dataframe, we got the average rating for each movie in rating column and name of the movie in title column. This does not make much sense for the movies who got several number of rating as compare to those who got very few!<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We need to look at the number of ratings as well. <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">So, let's create another column <span class="cm-comment">`n_ratings`</span> that tell us the number of ratings for each movie. Once again, groupby operating with count on the rating column!</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 113px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 125px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>So, in the above dataframe, we got the average rating for each movie in rating column and name of the movie in title column. This does not make much sense for the movies who got several number of rating as compare to those who got very few!<br>
We need to look at the number of ratings as well. <br>
So, let's create another column <code>n_ratings</code> that tell us the number of ratings for each movie. Once again, groupby operating with count on the rating column!</p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[12]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 570.111px; margin-bottom: -16px; border-right-width: 14px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">rating</span>[<span class="cm-string">'n_ratings'</span>] <span class="cm-operator">=</span> <span class="cm-variable">pd</span>.<span class="cm-property">DataFrame</span>(<span class="cm-variable">df</span>.<span class="cm-property">groupby</span>(<span class="cm-string">'title'</span>)[<span class="cm-string">'rating'</span>].<span class="cm-property">count</span>())</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">rating</span>.<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="height: 59px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[12]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right">
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
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 167px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>8</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.4445px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation" style=""><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">No, we have a dataframe <span class="cm-comment">`rating`</span> with three columns <span class="cm-comment">`title`</span>, <span class="cm-comment">`rating`</span> which is actually average of mean rating, and <span class="cm-comment">`n_rating`</span>. <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">5</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">6</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-2">## EDA </span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">7</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Let's do some EDA now!<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">8</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We do some imports first.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 167px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 179px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>No, we have a dataframe <code>rating</code> with three columns <code>title</code>, <code>rating</code> which is actually average of mean rating, and <code>n_rating</code>. <br></p>
<h2 id="EDA" data-toc-modified-id="EDA-1.3"><a class="toc-mod-link" id="EDA-1.3"></a><span class="toc-item-num">1.3&nbsp;&nbsp;</span>EDA<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#EDA">¶</a></h2>
<p>Let's do some EDA now!<br>
We do some imports first.</p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[13]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 247.181px; margin-bottom: -16px; border-right-width: 14px; min-height: 78px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-keyword">import</span> <span class="cm-variable">matplotlib</span>.<span class="cm-property">pyplot</span> <span class="cm-keyword">as</span> <span class="cm-variable">plt</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-keyword">import</span> <span class="cm-variable">seaborn</span> <span class="cm-keyword">as</span> <span class="cm-variable">sns</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-comment">#sns.set_style('white')</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-operator">%</span><span class="cm-variable">matplotlib</span> <span class="cm-variable">inline</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 78px;"></div><div class="CodeMirror-gutters" style="height: 92px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output" style="display: none;"></div><div class="output" style="display: none;"></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 79px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>3</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.4445px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">To learn from our dataset, let's plot two histograms side-by-side, one for No. of ratings for movies, n_ratings column, and the other for average rating which is rating column in the dataframe!<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We can creates two subplots and unpacks the output array immediately!</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 79px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 91px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>To learn from our dataset, let's plot two histograms side-by-side, one for No. of ratings for movies, n_ratings column, and the other for average rating which is rating column in the dataframe!<br></p>
<p>We can creates two subplots and unpacks the output array immediately!</p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[14]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 51.5972px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 485.667px; margin-bottom: -16px; border-right-width: 14px; min-height: 246px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>14</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.5972px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation" style=""><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">f</span>, (<span class="cm-variable">ax1</span>, <span class="cm-variable">ax2</span>) <span class="cm-operator">=</span> <span class="cm-variable">plt</span>.<span class="cm-property">subplots</span>(<span class="cm-variable">nrows</span><span class="cm-operator">=</span><span class="cm-number">1</span>, <span class="cm-variable">ncols</span><span class="cm-operator">=</span><span class="cm-number">2</span>, <span class="cm-variable">figsize</span><span class="cm-operator">=</span>(<span class="cm-number">10</span>,<span class="cm-number">4</span>))</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-comment"># For no. of ratings </span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">ax1</span>.<span class="cm-property">set_title</span>(<span class="cm-string">'No. of ratings'</span>)</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">5</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">ax1</span>.<span class="cm-property">hist</span>(<span class="cm-variable">rating</span>[<span class="cm-string">'n_ratings'</span>], <span class="cm-variable">bins</span> <span class="cm-operator">=</span><span class="cm-number">30</span>);</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">6</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">ax1</span>.<span class="cm-property">set_xlabel</span>(<span class="cm-string">'No of ratings for a movie'</span>)</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">7</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">ax1</span>.<span class="cm-property">set_ylabel</span>(<span class="cm-string">'No. of movies / frequency'</span>)</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">8</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">9</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">10</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-comment"># For rating</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">11</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">ax2</span>.<span class="cm-property">set_title</span>(<span class="cm-string">'Rating'</span>)</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">12</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">ax2</span>.<span class="cm-property">hist</span>(<span class="cm-variable">rating</span>[<span class="cm-string">'rating'</span>], <span class="cm-variable">bins</span> <span class="cm-operator">=</span><span class="cm-number">30</span>);</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">13</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">ax2</span>.<span class="cm-property">set_xlabel</span>(<span class="cm-string">'Rating (1 to 5)'</span>)</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">14</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">ax2</span>.<span class="cm-property">set_ylabel</span>(<span class="cm-string">'No. of movies / frequency'</span>)</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 246px;"></div><div class="CodeMirror-gutters" style="height: 260px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[14]:</bdi></div><div class="output_subarea output_text output_result"><pre>&lt;matplotlib.text.Text at 0x115b96898&gt;</pre></div></div><div class="output_area"><div class="run_this_cell"></div><div class="prompt"></div><div class="output_subarea output_png"><img src="data:image/png;base64,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%0AQmCC"></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 197px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>6</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.4446px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation" style=""><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">&amp;#9758; If we look at the "No. of Ratings" on the left, we learn that most of the movies have 0 or 1 number of ratings! So, either, people have not watched those movies and if they have watched, they did not rate them. The first argument somehow make sense, because, most of the time we prefer to watch only the famous movies! <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span> </span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">&amp;#9758; If we look at the "Rating, which is actually the mean rating" on the right, we may find that there are peaks at the whole numbers {1,2,3,4,5}. This is again a usual act, most of the time people rate the things with the whole numbers. <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Notice, there are some movies with average 5 star rating, they might be the outstanding movies or may got only few ratings. You can also point out some movies with really bad rating. However, most of the movies got average rating between 3 and 4. <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">5</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">6</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Let's check the relationship between rating and no. of rating with a seaborn <span class="cm-comment">`jointplot()`</span>.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 197px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 209px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>☞ If we look at the "No. of Ratings" on the left, we learn that most of the movies have 0 or 1 number of ratings! So, either, people have not watched those movies and if they have watched, they did not rate them. The first argument somehow make sense, because, most of the time we prefer to watch only the famous movies! <br> </p>
<p>☞ If we look at the "Rating, which is actually the mean rating" on the right, we may find that there are peaks at the whole numbers {1,2,3,4,5}. This is again a usual act, most of the time people rate the things with the whole numbers. <br>
Notice, there are some movies with average 5 star rating, they might be the outstanding movies or may got only few ratings. You can also point out some movies with really bad rating. However, most of the movies got average rating between 3 and 4. <br></p>
<p>Let's check the relationship between rating and no. of rating with a seaborn <code>jointplot()</code>.</p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[15]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 478.042px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">sns</span>.<span class="cm-property">jointplot</span>(<span class="cm-variable">x</span><span class="cm-operator">=</span><span class="cm-string">'rating'</span>,<span class="cm-variable">y</span><span class="cm-operator">=</span><span class="cm-string">'n_ratings'</span>,<span class="cm-variable">data</span><span class="cm-operator">=</span><span class="cm-variable">rating</span>,<span class="cm-variable">alpha</span><span class="cm-operator">=</span><span class="cm-number">0.5</span>)</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 42px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[15]:</bdi></div><div class="output_subarea output_text output_result"><pre>&lt;seaborn.axisgrid.JointGrid at 0x115a64be0&gt;</pre></div></div><div class="output_area"><div class="run_this_cell"></div><div class="prompt"></div><div class="output_subarea output_png"><img src="data:image/png;base64,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%0Agg=="></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 79px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>3</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">The joint plot is is making sense, more the number of rating a movie have, more average rating it gets.<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Good the movie is, more people will watch it and the movie will get more number of ratings or reviews. This is a normal act.<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We also see from the plot that the 1 or 2 stars movie have very few number of ratings.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 79px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 91px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>The joint plot is is making sense, more the number of rating a movie have, more average rating it gets.<br>
Good the movie is, more people will watch it and the movie will get more number of ratings or reviews. This is a normal act.<br>
We also see from the plot that the 1 or 2 stars movie have very few number of ratings.</p>
</div></div></div><div class="cell text_cell rendered collapsible_headings_ellipsis unselected" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h2"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 100px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>4</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 20.4444px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-2">## Recommender System for similar movie</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Now we got some understanding of our data, let's move on to develop and simple recommender system that can recommend similar movies to the user.<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Let's check the head of the original data again.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 100px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 112px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h2 id="Recommender-System-for-similar-movie" data-toc-modified-id="Recommender-System-for-similar-movie-1.4"><a class="toc-mod-link" id="Recommender-System-for-similar-movie-1.4"></a><span class="toc-item-num">1.4&nbsp;&nbsp;</span>Recommender System for similar movie<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#Recommender-System-for-similar-movie">¶</a></h2>
<p>Now we got some understanding of our data, let's move on to develop and simple recommender system that can recommend similar movies to the user.<br></p>
<p>Let's check the head of the original data again.</p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[16]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 77.6667px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">df</span>.<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 42px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[16]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right">
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
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 282px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>13</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.4446px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation" style=""><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">To move on, let's create a matrix that will have the userId on one axis (index) and the title on another axis (columns) whereas, rating as its value. In the way, each cell will consist of the rating that the user gave to a certain movie. <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">So, we need userId, title and rating columns for such matrix. We are going to use <span class="cm-comment">`pivot_table()`</span> method to get our required matrix. <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">5</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Our parameter for the <span class="cm-comment">`pivot_table()`</span> will be: <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">6</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">7</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable-2">* </span><span class="cm-comment cm-variable-2">`index = userId`</span><span class="cm-variable-2"> </span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">8</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable-2">* </span><span class="cm-comment cm-variable-2">`columns = title`</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">9</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable-2">* </span><span class="cm-comment cm-variable-2">`values = rating`</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">10</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">11</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-em">*&amp;#9758; </span><span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">font</span> <span class="cm-attribute">style</span>=<span class="cm-string">"font-size:12px;color:green;"</span><span class="cm-tag cm-bracket">&gt;</span>Remember, if there is no rating for a movie from the user, there will be `NaN`, so **lots of `NaN` values!, right?** *<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;&lt;/</span><span class="cm-tag">font</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">12</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">13</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Let's do the task and call the new matrix as <span class="cm-comment">`rating_mat`</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 282px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 294px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>To move on, let's create a matrix that will have the userId on one axis (index) and the title on another axis (columns) whereas, rating as its value. In the way, each cell will consist of the rating that the user gave to a certain movie. <br></p>
<p>So, we need userId, title and rating columns for such matrix. We are going to use <code>pivot_table()</code> method to get our required matrix. <br></p>
<p>Our parameter for the <code>pivot_table()</code> will be: <br></p>
<ul>
<li><code>index = userId</code> </li>
<li><code>columns = title</code></li>
<li><code>values = rating</code></li>
</ul>
<p><em>☞ <font style="font-size: 12px ; color: green">Remember, if there is no rating for a movie from the user, there will be <code>NaN</code>, so *</font></em>lots of <code>NaN</code> values!, right?** *<br></p>
<p>Let's do the task and call the new matrix as <code>rating_mat</code></p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[17]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 347.25px; margin-bottom: -16px; border-right-width: 14px; min-height: 62px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div><div class="CodeMirror-gutter-elt" style="left: 33px; width: 12px;"><div class="CodeMirror-foldgutter-open CodeMirror-guttermarker-subtle"></div></div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">rating_mat</span> <span class="cm-operator">=</span> <span class="cm-variable">df</span>.<span class="cm-property">pivot_table</span>(<span class="cm-variable">index</span><span class="cm-operator">=</span><span class="cm-string">'userId'</span>,</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">                            <span class="cm-variable">columns</span><span class="cm-operator">=</span><span class="cm-string">'title'</span>,</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">                            <span class="cm-variable">values</span><span class="cm-operator">=</span><span class="cm-string">'rating'</span>)</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 62px;"></div><div class="CodeMirror-gutters" style="height: 76px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output" style="display: none;"></div><div class="output" style="display: none;"></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[18]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 139px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">rating_mat</span>.<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 42px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[18]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right">
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
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 96px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>4</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.4446px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">As already mentioned, we have lots of missing values, because, most of the people have not watched those movies or, if watched, they have not rated them!<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-strong">**Let's check the most rated movies once again from our rating dataframne.**</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 96px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 108px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>As already mentioned, we have lots of missing values, because, most of the people have not watched those movies or, if watched, they have not rated them!<br></p>
<p><strong>Let's check the most rated movies once again from our rating dataframne.</strong></p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[19]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59985px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 447.278px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">rating</span>.<span class="cm-property">sort_values</span>(<span class="cm-string">'n_ratings'</span>, <span class="cm-variable">ascending</span><span class="cm-operator">=</span><span class="cm-keyword">False</span>).<span class="cm-property">head</span>(<span class="cm-number">10</span>)</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 42px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[19]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right">
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
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59766px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 113px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>6</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation" style=""><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Let's select any 2 movies, for example:</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable-2">* No. 1: &nbsp;</span><span class="cm-strong cm-variable-2">**Forrest Gump (1994)**</span><span class="cm-variable-2"> and </span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable-2">* No. 7: &nbsp;</span><span class="cm-strong cm-variable-2">**Matrix, The (1999)**</span><span class="cm-variable-2"> </span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">5</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">6</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">and check there category / genre. <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 113px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 125px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>Let's select any 2 movies, for example:</p>
<ul>
<li>No. 1:  <strong>Forrest Gump (1994)</strong> and </li>
<li>No. 7:  <strong>Matrix, The (1999)</strong> </li>
</ul>
<p>and check there category / genre. <br></p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[20]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 362.639px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">movies</span>[<span class="cm-variable">movies</span>[<span class="cm-string">'title'</span>]<span class="cm-operator">==</span><span class="cm-string">'Forrest Gump (1994)'</span>]</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 42px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[20]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right">
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
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[21]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59985px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 354.944px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">movies</span>[<span class="cm-variable">movies</span>[<span class="cm-string">'title'</span>]<span class="cm-operator">==</span><span class="cm-string">'Matrix, The (1999)'</span>]</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 42px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[21]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right">
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
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 113px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>5</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation" style=""><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">So, the <span class="cm-strong">**Forrest Gump (1994) is a Comedy drama movie**</span> where as <span class="cm-strong">**Matrix is Sci-Fic Action etc**</span><span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Let's grab their rating from our <span class="cm-comment">`rating_mat`</span> and check their heads.<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">5</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We can get the rating for <span class="cm-strong">**Forrest Gump (1994) in FG_user_ratings**</span> and rating for <span class="cm-strong">**Matrix, The (1999) in Matrix_user_ratings**</span>.</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 113px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 125px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>So, the <strong>Forrest Gump (1994) is a Comedy drama movie</strong> where as <strong>Matrix is Sci-Fic Action etc</strong><br></p>
<p>Let's grab their rating from our <code>rating_mat</code> and check their heads.<br></p>
<p>We can get the rating for <strong>Forrest Gump (1994) in FG_user_ratings</strong> and rating for <strong>Matrix, The (1999) in Matrix_user_ratings</strong>.</p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[22]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 424.222px; margin-bottom: -16px; border-right-width: 14px; min-height: 95px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation" style=""><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div><div class="CodeMirror-gutter-elt" style="left: 33px; width: 12px;"><div class="CodeMirror-foldgutter-open CodeMirror-guttermarker-subtle"></div></div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-comment">#Getting ratings from rating_mat</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">FG_user_ratings</span> <span class="cm-operator">=</span> <span class="cm-variable">rating_mat</span>[<span class="cm-string">'Forrest Gump (1994)'</span>]</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">Matrix_user_ratings</span> <span class="cm-operator">=</span> <span class="cm-variable">rating_mat</span>[<span class="cm-string">'Matrix, The (1999)'</span>]</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-comment">#Displaying the heads</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">5</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">FG_user_ratings</span>.<span class="cm-property">head</span>(), <span class="cm-variable">Matrix_user_ratings</span>.<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 95px;"></div><div class="CodeMirror-gutters" style="height: 109px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[22]:</bdi></div><div class="output_subarea output_text output_result"><pre>(userId
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
 Name: Matrix, The (1999), dtype: float64)</pre></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 180px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>7</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation" style=""><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">So, we got the user ratings for the selected movies. <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Now, we want to know how these movies are correlated to the other movies in the dataframe. <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">pandas had a built-in function <span class="cm-comment">`corrwith()`</span> which Compute the pairwise correlation between rows or columns of two DataFrame objects. <span class="cm-em">*</span><span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">font</span> <span class="cm-attribute">style</span>=<span class="cm-string">"font-size:12px;color:green;"</span><span class="cm-tag cm-bracket">&gt;</span>(shift+tab for doc string)<span class="cm-tag cm-bracket">&lt;/</span><span class="cm-tag">font</span><span class="cm-tag cm-bracket">&gt;</span><span class="cm-em">*</span>.<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">5</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Let's see how the user rating of Forrest Gump (FG_user_ratings) is correlated with the user rating of all other movies in the <span class="cm-comment">`rating_mat`</span>!<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">6</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">7</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We are computing the correlation of <span class="cm-strong">**FG_user_ratings**</span> to the user rating or user behavior for all other movies and passing that to <span class="cm-strong">**similar_to_FG**</span>. We will also do the same for <span class="cm-strong">**Matrix**</span> at the same time!</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 180px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 192px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>So, we got the user ratings for the selected movies. <br>
Now, we want to know how these movies are correlated to the other movies in the dataframe. <br>
pandas had a built-in function <code>corrwith()</code> which Compute the pairwise correlation between rows or columns of two DataFrame objects. <em><font style="font-size: 12px ; color: green">(shift+tab for doc string)</font></em>.<br></p>
<p>Let's see how the user rating of Forrest Gump (FG_user_ratings) is correlated with the user rating of all other movies in the <code>rating_mat</code>!<br></p>
<p>We are computing the correlation of <strong>FG_user_ratings</strong> to the user rating or user behavior for all other movies and passing that to <strong>similar_to_FG</strong>. We will also do the same for <strong>Matrix</strong> at the same time!</p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[23]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 485.667px; margin-bottom: -16px; border-right-width: 14px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">similar_to_FG</span> <span class="cm-operator">=</span> <span class="cm-variable">rating_mat</span>.<span class="cm-property">corrwith</span>(<span class="cm-variable">FG_user_ratings</span>)<span class="cm-comment">#.head(10)</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">similar_to_matrix</span> <span class="cm-operator">=</span> <span class="cm-variable">rating_mat</span>.<span class="cm-property">corrwith</span>(<span class="cm-variable">Matrix_user_ratings</span>)</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="height: 59px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to scroll output; double click to hide"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt"></div><div class="output_subarea output_text output_stream output_stderr"><pre>/anaconda/lib/python3.6/site-packages/numpy/lib/function_base.py:3154: RuntimeWarning: Degrees of freedom &lt;= 0 for slice
  c = cov(x, y, rowvar)
/anaconda/lib/python3.6/site-packages/numpy/lib/function_base.py:3088: RuntimeWarning: divide by zero encountered in double_scalars
  c *= 1. / np.float64(fact)
</pre></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59766px; left: 39.5972px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 164px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>7</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.59723px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation" style=""><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-em">*</span><span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">font</span> <span class="cm-attribute">style</span>=<span class="cm-string">"font-size:12px;color:green;"</span><span class="cm-tag cm-bracket">&gt;</span>Don't worry if you get the warning, its just a pandas warning.<span class="cm-tag cm-bracket">&lt;/</span><span class="cm-tag">font</span><span class="cm-tag cm-bracket">&gt;</span><span class="cm-em">*</span><span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Now, if we display the head of the dataframe for <span class="cm-strong">**</span><span class="cm-strong cm-comment">`similar_to_FG`</span><span class="cm-strong">**</span> and <span class="cm-strong">**</span><span class="cm-strong cm-comment">`similar_to_matrix`</span><span class="cm-strong">**</span>, we will see NaN. <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">5</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We need to clean the data for null value using <span class="cm-comment">`dropna()`</span>. First, We can create a dataframe instead of series so that it look little nicer, and then we will deal with NaN!<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">6</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">7</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">In order to create a dataframe, we need to pass <span class="cm-comment">`similar_to_FG`</span> and <span class="cm-comment">`similar_to_matrix`</span> to pandas <span class="cm-comment">`DataFrame()`</span>. We can set the column name as <span class="cm-comment">`correlation`</span>!</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 164px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 176px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p><em><font style="font-size: 12px ; color: green">Don't worry if you get the warning, its just a pandas warning.</font></em><br></p>
<p>Now, if we display the head of the dataframe for <strong><code>similar_to_FG</code></strong> and <strong><code>similar_to_matrix</code></strong>, we will see NaN. <br></p>
<p>We need to clean the data for null value using <code>dropna()</code>. First, We can create a dataframe instead of series so that it look little nicer, and then we will deal with NaN!<br></p>
<p>In order to create a dataframe, we need to pass <code>similar_to_FG</code> and <code>similar_to_matrix</code> to pandas <code>DataFrame()</code>. We can set the column name as <code>correlation</code>!</p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[24]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.6001px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 500.778px; margin-bottom: -16px; border-right-width: 14px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">corr_FG</span> <span class="cm-operator">=</span> <span class="cm-variable">pd</span>.<span class="cm-property">DataFrame</span>(<span class="cm-variable">similar_to_FG</span>, <span class="cm-variable">columns</span> <span class="cm-operator">=</span> [<span class="cm-string">'correlation'</span>])</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">corr_FG</span>.<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="height: 59px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[24]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right">
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
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 28px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Let's drop NaN and check the head again!</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 40px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>Let's drop NaN and check the head again!</p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[25]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59998px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 224.083px; margin-bottom: -16px; border-right-width: 14px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">corr_FG</span>.<span class="cm-property">dropna</span>(<span class="cm-variable">inplace</span><span class="cm-operator">=</span><span class="cm-keyword">True</span>)</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">corr_FG</span>.<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="height: 59px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[25]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right">
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
      <th>$9.99 (2008)</th>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>'burbs, The (1989)</th>
      <td>0.044946</td>
    </tr>
    <tr>
      <th>(500) Days of Summer (2009)</th>
      <td>0.624458</td>
    </tr>
    <tr>
      <th>*batteries not included (1987)</th>
      <td>0.603023</td>
    </tr>
    <tr>
      <th>...And Justice for All (1979)</th>
      <td>0.173422</td>
    </tr>
  </tbody>
</table>
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 28px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Let's do the same for matrix (similar_to_matrix)</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 40px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>Let's do the same for matrix (similar_to_matrix)</p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[26]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59998px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 562.722px; margin-bottom: -16px; border-right-width: 14px; min-height: 62px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">corr_matrix</span> <span class="cm-operator">=</span> <span class="cm-variable">pd</span>.<span class="cm-property">DataFrame</span>(<span class="cm-variable">similar_to_matrix</span>, <span class="cm-variable">columns</span> <span class="cm-operator">=</span> [<span class="cm-string">'correlation'</span>])</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">corr_matrix</span>.<span class="cm-property">dropna</span>(<span class="cm-variable">inplace</span><span class="cm-operator">=</span><span class="cm-keyword">True</span>)</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">corr_matrix</span>.<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 62px;"></div><div class="CodeMirror-gutters" style="height: 76px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[26]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right">
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
      <th>$9.99 (2008)</th>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>'burbs, The (1989)</th>
      <td>0.056624</td>
    </tr>
    <tr>
      <th>(500) Days of Summer (2009)</th>
      <td>0.368837</td>
    </tr>
    <tr>
      <th>*batteries not included (1987)</th>
      <td>0.743955</td>
    </tr>
    <tr>
      <th>...And Justice for All (1979)</th>
      <td>-0.610170</td>
    </tr>
  </tbody>
</table>
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59717px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 130px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>4</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.4446px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">So, in the recently created dataframes (corr_FG and corr_matrix), the index is the title of the movie whereas the correlation column tells how correlated the user rating of Forrest Gump and Matrix are to the user rating of the other movies. <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">In principle, if we sort our dataframes by correlation, we should get the most similar movies to Forrest Gump and Matrix in order, in the respective dataframes. <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Let's see if this works for matrix movie only. (you can do the same for Forrest Gump after this)</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 130px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 142px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>So, in the recently created dataframes (corr_FG and corr_matrix), the index is the title of the movie whereas the correlation column tells how correlated the user rating of Forrest Gump and Matrix are to the user rating of the other movies. <br>
In principle, if we sort our dataframes by correlation, we should get the most similar movies to Forrest Gump and Matrix in order, in the respective dataframes. <br></p>
<p>Let's see if this works for matrix movie only. (you can do the same for Forrest Gump after this)</p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[27]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59998px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 493.458px; margin-bottom: -16px; border-right-width: 14px; min-height: 28px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">corr_matrix</span>.<span class="cm-property">sort_values</span>(<span class="cm-string">'correlation'</span>,<span class="cm-variable">ascending</span><span class="cm-operator">=</span><span class="cm-keyword">False</span>).<span class="cm-property">head</span>(<span class="cm-number">10</span>)</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="height: 42px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[27]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right">
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
      <th>Becket (1964)</th>
      <td>1.0</td>
    </tr>
    <tr>
      <th>Musketeer, The (2001)</th>
      <td>1.0</td>
    </tr>
    <tr>
      <th>Allan Quatermain and the Lost City of Gold (1987)</th>
      <td>1.0</td>
    </tr>
    <tr>
      <th>Honeysuckle Rose (a.k.a. On the Road Again) (1980)</th>
      <td>1.0</td>
    </tr>
    <tr>
      <th>Hope and Glory (1987)</th>
      <td>1.0</td>
    </tr>
    <tr>
      <th>Shadow of the Thin Man (1941)</th>
      <td>1.0</td>
    </tr>
    <tr>
      <th>Clean and Sober (1988)</th>
      <td>1.0</td>
    </tr>
    <tr>
      <th>Hotel Transylvania 2 (2015)</th>
      <td>1.0</td>
    </tr>
    <tr>
      <th>Mr. Blandings Builds His Dream House (1948)</th>
      <td>1.0</td>
    </tr>
  </tbody>
</table>
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59766px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 147px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>6</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.4443px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation" style=""><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">This is perfect correlation! you may not heard about most of these movies but the correlation we are getting is perfect. <span class="cm-strong">**The results does not make much sense.**</span> <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We need to fix this and we know what the reason is. Most likely, these movies are watched only once by the same users who also watched Matrix and rated both with similar stars. <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">5</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">To fix this, we can set a <span class="cm-strong">**threshold value for the ratings**</span><span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">6</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-strong">**Let's re-plot a histogram for n_rating to see which could be a good threshold value for no of ratings!**</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 147px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 159px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>This is perfect correlation! you may not heard about most of these movies but the correlation we are getting is perfect. <strong>The results does not make much sense.</strong> <br></p>
<p>We need to fix this and we know what the reason is. Most likely, these movies are watched only once by the same users who also watched Matrix and rated both with similar stars. <br></p>
<p>To fix this, we can set a <strong>threshold value for the ratings</strong><br>
<strong>Let's re-plot a histogram for n_rating to see which could be a good threshold value for no of ratings!</strong></p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[28]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.60001px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 308.722px; margin-bottom: -16px; border-right-width: 14px; min-height: 62px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">plt</span>.<span class="cm-property">hist</span>(<span class="cm-variable">rating</span>[<span class="cm-string">'n_ratings'</span>], <span class="cm-variable">bins</span><span class="cm-operator">=</span><span class="cm-number">50</span>);</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">plt</span>.<span class="cm-property">ylim</span>(<span class="cm-number">0</span>,<span class="cm-number">500</span>);</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">plt</span>.<span class="cm-property">xlim</span>(<span class="cm-number">0</span>,<span class="cm-number">200</span>);</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 62px;"></div><div class="CodeMirror-gutters" style="height: 76px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt"></div><div class="output_subarea output_png"><img src="data:image/png;base64,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%0ApS9JBfl/imkV34EoxygAAAAASUVORK5CYII="></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59766px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 180px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>7</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation" style=""><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">So, we see that the drop is significant after n_rating = 50.<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We can select 50 as a minimum no. of rating in order to be considered into our recommender system. (<span class="cm-em">*you can play with different numbers to see how the results varies)*</span><span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">5</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Let's sort the value again with the condition (<span class="cm-comment">`n_rating &gt;50`</span>) and also join the n_ratings column from <span class="cm-comment">`rating`</span> dataframe to <span class="cm-comment">`corr_matrix`</span> dataframe and apply the condition for <span class="cm-comment">`n_rating &gt; 50`</span><span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">6</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">7</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">font</span> <span class="cm-attribute">style</span>=<span class="cm-string">"font-size:12px;color:green;"</span><span class="cm-tag cm-bracket">&gt;</span>*default join is a left join, use calling frame's index (or column if on is specified), this is a good choice here as we have title as index*<span class="cm-tag cm-bracket">&lt;/</span><span class="cm-tag">font</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 180px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 192px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>So, we see that the drop is significant after n_rating = 50.<br></p>
<p>We can select 50 as a minimum no. of rating in order to be considered into our recommender system. (<em>you can play with different numbers to see how the results varies)</em><br></p>
<p>Let's sort the value again with the condition (<code>n_rating &gt;50</code>) and also join the n_ratings column from <code>rating</code> dataframe to <code>corr_matrix</code> dataframe and apply the condition for <code>n_rating &gt; 50</code><br></p>
<p><font style="font-size: 12px ; color: green"><em>default join is a left join, use calling frame's index (or column if on is specified), this is a good choice here as we have title as index</em></font></p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[29]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.60001px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 401.111px; margin-bottom: -16px; border-right-width: 14px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">corr_matrix</span> <span class="cm-operator">=</span> <span class="cm-variable">corr_matrix</span>.<span class="cm-property">join</span>(<span class="cm-variable">rating</span>[<span class="cm-string">'n_ratings'</span>])</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">corr_matrix</span>.<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="height: 59px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[29]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right">
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
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell rendered unselected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59668px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 28px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">We need to sort the values in order from high to low!<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 28px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 40px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>We need to sort the values in order from high to low!<br></p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[30]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.60001px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 416.514px; margin-bottom: -16px; border-right-width: 14px; min-height: 45px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div><div class="CodeMirror-gutter-elt" style="left: 33px; width: 12px;"><div class="CodeMirror-foldgutter-open CodeMirror-guttermarker-subtle"></div></div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">corr_matrix</span>[<span class="cm-variable">corr_matrix</span>[<span class="cm-string">'n_ratings'</span>]<span class="cm-operator">&gt;</span><span class="cm-number">50</span>].<span class="cm-property">sort_values</span>(</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">    <span class="cm-string">'correlation'</span>,<span class="cm-variable">ascending</span><span class="cm-operator">=</span><span class="cm-keyword">False</span>).<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 45px;"></div><div class="CodeMirror-gutters" style="height: 59px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[30]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right">
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
      <th>Matrix, The (1999)</th>
      <td>1.000000</td>
      <td>259</td>
    </tr>
    <tr>
      <th>Star Trek: Generations (1994)</th>
      <td>0.509976</td>
      <td>114</td>
    </tr>
    <tr>
      <th>Prestige, The (2006)</th>
      <td>0.458716</td>
      <td>52</td>
    </tr>
    <tr>
      <th>Lord of the Rings: The Two Towers, The (2002)</th>
      <td>0.451960</td>
      <td>188</td>
    </tr>
    <tr>
      <th>Lord of the Rings: The Fellowship of the Ring, The (2001)</th>
      <td>0.441993</td>
      <td>200</td>
    </tr>
  </tbody>
</table>
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell rendered selected" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59766px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 130px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>5</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 16.4443px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation" style=""><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Now the results make much more sense! Matrix has the perfect correlation to itself. The Star Trek is the closely correlated with Matrix!<span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable-2">* Another important thing to remember, lots of time the recommender systems suggest a really popular movie against the popular one you have watched, even if the category is not similar!</span><span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">5</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Let's do the same for "Forrest Gump"!</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 130px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 142px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p>Now the results make much more sense! Matrix has the perfect correlation to itself. The Star Trek is the closely correlated with Matrix!<br></p>
<ul>
<li>Another important thing to remember, lots of time the recommender systems suggest a really popular movie against the popular one you have watched, even if the category is not similar!<br></li>
</ul>
<p>Let's do the same for "Forrest Gump"!</p>
</div></div></div><div class="cell code_cell unselected rendered" tabindex="2"><div class="input"><div class="run_this_cell" title="Run this cell"><i class="fa-step-forward fa"></i></div><div class="prompt input_prompt"><bdi>In</bdi>&nbsp;[31]:</div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-ipython"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.60004px; left: 51.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 46px; min-width: 354.931px; margin-bottom: -16px; border-right-width: 14px; min-height: 62px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>1</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33331px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">corr_FG</span> <span class="cm-operator">=</span> <span class="cm-variable">corr_FG</span>.<span class="cm-property">join</span>(<span class="cm-variable">rating</span>[<span class="cm-string">'n_ratings'</span>])</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div><div class="CodeMirror-gutter-elt" style="left: 33px; width: 12px;"><div class="CodeMirror-foldgutter-open CodeMirror-guttermarker-subtle"></div></div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-variable">corr_FG</span>[<span class="cm-variable">corr_FG</span>[<span class="cm-string">'n_ratings'</span>]<span class="cm-operator">&gt;</span><span class="cm-number">50</span>].<span class="cm-property">sort_values</span>(</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -46px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">    <span class="cm-string">'correlation'</span>,<span class="cm-variable">ascending</span><span class="cm-operator">=</span><span class="cm-keyword">False</span>).<span class="cm-property">head</span>()</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 14px; width: 1px; border-bottom: 0px solid transparent; top: 62px;"></div><div class="CodeMirror-gutters" style="height: 76px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div><div class="CodeMirror-gutter CodeMirror-foldgutter"></div></div></div></div></div></div></div><div class="output_wrapper"><div class="out_prompt_overlay prompt" title="click to expand output; double click to hide output"></div><div class="output"><div class="output_area"><div class="run_this_cell"></div><div class="prompt output_prompt"><bdi>Out[31]:</bdi></div><div class="output_subarea output_html rendered_html output_result"><div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right">
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
</div></div></div></div><div class="btn btn-default output_collapsed" title="click to expand output" style="display: none;">. . .</div></div></div><div class="cell text_cell unselected rendered collapsible_headings_ellipsis" tabindex="2"><div class="prompt input_prompt"><div class="collapsible_headings_toggle" style="color: rgb(170, 170, 170);"><div class="h2"><i class="fa fa-fw fa-caret-down"></i></div></div></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59766px; left: 39.3333px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 49px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>2</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.33334px; top: 0px; height: 20.4444px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation"><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-2">## Excellent work!</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">I hope that you have enjoyed the Recommender Systems section. <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 49px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 61px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><h2 id="Excellent-work!" data-toc-modified-id="Excellent-work!-1.5"><a class="toc-mod-link" id="Excellent-work!-1.5"></a><span class="toc-item-num">1.5&nbsp;&nbsp;</span>Excellent work!<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#Excellent-work!">¶</a></h2>
<p>I hope that you have enjoyed the Recommender Systems section. <br></p>
</div></div></div><div class="cell text_cell unselected rendered" tabindex="2"><div class="prompt input_prompt"></div><div class="inner_cell"><div class="ctb_hideshow"><div class="celltoolbar"></div></div><div class="input_area"><div class="CodeMirror cm-s-default CodeMirror-wrap"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 5.59766px; left: 39.5972px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" tabindex="0" style="position: absolute; bottom: -1em; padding: 0px; width: 1000px; height: 1em; outline: none;"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 34px; padding-right: 0px; padding-bottom: 0px; margin-bottom: -18px; border-right-width: 12px; min-height: 647px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines" role="presentation"><div role="presentation" style="position: relative; outline: none;"><div class="CodeMirror-measure"><div class="CodeMirror-linenumber CodeMirror-gutter-elt"><div>27</div></div></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors"><div class="CodeMirror-cursor" style="left: 5.59723px; top: 0px; height: 16.8889px;">&nbsp;</div></div><div class="CodeMirror-code" role="presentation" style=""><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-2">## Interested to learn and play with more dataset to develop you own Recommender Systems ?</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;">Below are some very useful links to the datasets (<span class="cm-em">*the links are up and working till today, sometimes, they are broken. If you find any link broken, please send me a message or post it in Q &amp; A section. You best bet is to google the dataframe, most of the time you will find the new link and would be able to download the data from there*</span>). <span class="cm-tag cm-bracket">&lt;</span><span class="cm-tag">br</span><span class="cm-tag cm-bracket">&gt;</span>The datasets for recommender systems are quote large in most of the cases. You can develop your own Recommender systems and see how the things work on different datasets. </span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">5</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">6</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-link">[Chicago Entree - Food Ratings Data Sets at UCI Repository]</span><span class="cm-string cm-url">(http://archive.ics.uci.edu/ml/datasets/Entree+Chicago+Recommendation+Data)</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">7</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">8</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-link">[Nursing Home - Provider Ratings Data Set]</span><span class="cm-string cm-url">(http://data.medicare.gov/dataset/Nursing-Home-Compare-Provider-Ratings/mufm-vy8d)</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">9</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">10</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-link">[MovieLens - Movie Recommendation Data Sets]</span><span class="cm-string cm-url">(https://grouplens.org/datasets/movielens/)</span> - The one we have used above.</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">11</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">12</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-link">[Yahoo! - Movie, Music, and Images Ratings Data Sets]</span><span class="cm-string cm-url">(https://webscope.sandbox.yahoo.com/catalog.php?datatype=r)</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">13</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">14</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-link">[Jester - Movie Ratings Data Sets (Collaborative Filtering Dataset)]</span><span class="cm-string cm-url">(http://www.ieor.berkeley.edu/~goldberg/jester-data/)</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">15</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">16</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-link">[Cornell University - Movie-review data for use in sentiment-analysis experiments]</span><span class="cm-string cm-url">(http://www.cs.cornell.edu/people/pabo/movie-review-data/)</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">17</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">18</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-link">[Last.fm - Music Recommendation Data Sets]</span><span class="cm-string cm-url">(http://www.dtic.upf.edu/~ocelma/MusicRecommendationDataset/index.html)</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">19</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">20</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-link">[National University of Singapore - Scholarly Paper Recommendation]</span><span class="cm-string cm-url">(http://www.comp.nus.edu.sg/~sugiyama/SchPaperRecData.html)</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">21</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">22</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-link">[Dating website recommendation (collaborative filtering)]</span><span class="cm-string cm-url">(http://www.occamslab.com/petricek/data/)</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">23</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">24</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-link">[Institut für Informatik, Universität Freiburg - Book Ratings Data Sets]</span><span class="cm-string cm-url">(http://www.informatik.uni-freiburg.de/~cziegler/BX/)</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">25</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">26</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span cm-text="">​</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -34px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">27</div></div><pre class=" CodeMirror-line " role="presentation"><span role="presentation" style="padding-right: 0.1px;"><span class="cm-header cm-header-2">## Good Luck! </span></span></pre></div></div></div></div></div></div><div style="position: absolute; height: 12px; width: 1px; border-bottom: 0px solid transparent; top: 647px;"></div><div class="CodeMirror-gutters" style="left: 0px; height: 659px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 33px;"></div></div></div></div></div><div class="text_cell_render rendered_html" tabindex="-1"><p><br><br><br><br><br><br></p>
<h2 id="Interested-to-learn-and-play-with-more-dataset-to-develop-you-own-Recommender-Systems-?" data-toc-modified-id="Interested-to-learn-and-play-with-more-dataset-to-develop-you-own-Recommender-Systems-?-1.6"><a class="toc-mod-link" id="Interested-to-learn-and-play-with-more-dataset-to-develop-you-own-Recommender-Systems-?-1.6"></a><span class="toc-item-num">1.6&nbsp;&nbsp;</span>Interested to learn and play with more dataset to develop you own Recommender Systems ?<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#Interested-to-learn-and-play-with-more-dataset-to-develop-you-own-Recommender-Systems-?">¶</a></h2>
<p>Below are some very useful links to the datasets (<em>the links are up and working till today, sometimes, they are broken. If you find any link broken, please send me a message or post it in Q &amp; A section. You best bet is to google the dataframe, most of the time you will find the new link and would be able to download the data from there</em>). <br>The datasets for recommender systems are quote large in most of the cases. You can develop your own Recommender systems and see how the things work on different datasets. </p>
<p><a href="http://archive.ics.uci.edu/ml/datasets/Entree+Chicago+Recommendation+Data" target="_blank">Chicago Entree - Food Ratings Data Sets at UCI Repository</a></p>
<p><a href="http://data.medicare.gov/dataset/Nursing-Home-Compare-Provider-Ratings/mufm-vy8d" target="_blank">Nursing Home - Provider Ratings Data Set</a></p>
<p><a href="https://grouplens.org/datasets/movielens/" target="_blank">MovieLens - Movie Recommendation Data Sets</a> - The one we have used above.</p>
<p><a href="https://webscope.sandbox.yahoo.com/catalog.php?datatype=r" target="_blank">Yahoo! - Movie, Music, and Images Ratings Data Sets</a></p>
<p><a href="http://www.ieor.berkeley.edu/~goldberg/jester-data/" target="_blank">Jester - Movie Ratings Data Sets (Collaborative Filtering Dataset)</a></p>
<p><a href="http://www.cs.cornell.edu/people/pabo/movie-review-data/" target="_blank">Cornell University - Movie-review data for use in sentiment-analysis experiments</a></p>
<p><a href="http://www.dtic.upf.edu/~ocelma/MusicRecommendationDataset/index.html" target="_blank">Last.fm - Music Recommendation Data Sets</a></p>
<p><a href="http://www.comp.nus.edu.sg/~sugiyama/SchPaperRecData.html" target="_blank">National University of Singapore - Scholarly Paper Recommendation</a></p>
<p><a href="http://www.occamslab.com/petricek/data/" target="_blank">Dating website recommendation (collaborative filtering)</a></p>
<p><a href="http://www.informatik.uni-freiburg.de/~cziegler/BX/" target="_blank">Institut für Informatik, Universität Freiburg - Book Ratings Data Sets</a></p>
<h2 id="Good-Luck!" data-toc-modified-id="Good-Luck!-1.7"><a class="toc-mod-link" id="Good-Luck!-1.7"></a><span class="toc-item-num">1.7&nbsp;&nbsp;</span>Good Luck!<a class="anchor-link" href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#Good-Luck!">¶</a></h2>
</div></div></div></div><div class="end_space"></div></div>
        <div id="tooltip" class="ipython_tooltip" style="display:none"><div class="tooltipbuttons"><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#" role="button" class="ui-button"><span class="ui-icon ui-icon-close">Close</span></a><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#" class="ui-corner-all" role="button" id="expanbutton" title="Grow the tooltip vertically (press shift-tab twice)"><span class="ui-icon ui-icon-plus">Expand</span></a><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#" role="button" class="ui-button" title="show the current docstring in pager (press shift-tab 4 times)"><span class="ui-icon ui-icon-arrowstop-l-n">Open in Pager</span></a><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#" role="button" class="ui-button" title="Tooltip will linger for 10 seconds while you type" style="display: none;"><span class="ui-icon ui-icon-clock">Close</span></a></div><div class="pretooltiparrow"></div><div class="tooltiptext smalltooltip"></div></div>
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


<div style="position: absolute; width: 0px; height: 0px; overflow: hidden; padding: 0px; border: 0px; margin: 0px;"><div id="MathJax_Font_Test" style="position: absolute; visibility: hidden; top: 0px; left: 0px; width: auto; min-width: 0px; max-width: none; padding: 0px; border: 0px; margin: 0px; white-space: nowrap; text-align: left; text-indent: 0px; text-transform: none; line-height: normal; letter-spacing: normal; word-spacing: normal; font-size: 40px; font-weight: normal; font-style: normal;"></div></div><style>#toc li > span:hover { background-color: #DAA520 }
.toc-item-highlight-select  {background-color: #FFD700}
.toc-item-highlight-execute  {background-color: #FF0000}
.toc-item-highlight-execute.toc-item-highlight-select   {background-color: #FFD700}div#menubar-container, div#header-container {
width: auto;
padding-left: 20px; }#toc-wrapper { background-color: #FFFFFF}
#toc a, #navigate_menu a, .toc { color: #333333}#toc-wrapper .toc-item-num { color: #000000}.sidebar-wrapper { border-color: #EEEEEE}.highlight_on_scroll { border-left: solid 4px #2447f0}</style><div id="varInspector-wrapper" class="ui-draggable ui-resizable varInspector-float-wrapper" style="position: fixed; display: none; max-height: 653px;"><div id="varInspector-header" class="header">Variable Inspector <a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#" class="kill-btn" title="Close window">[x]</a><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#" class="hide-btn" title="Hide Variable Inspector">[-]</a><a href="http://localhost:8888/notebooks/Documents/Course-Material/Course_Material/S_17_Rec_Sys/RSs_Python.ipynb#" class="reload-btn" title="Reload Variable Inspector">  ↻</a><span>&nbsp;&nbsp;</span><span>&nbsp;&nbsp;</span></div><div id="varInspector" class="varInspector" style="height: 92.222px; max-height: 633px;"><div class="inspector"><table class="table fixed table-condensed table-nonfluid tablesorter tablesorter-default" role="grid"><colgroup><col>  <col><col></colgroup><thead><tr role="row" class="tablesorter-headerRow"><th data-column="0" class="tablesorter-header tablesorter-headerUnSorted" tabindex="0" scope="col" role="columnheader" aria-disabled="false" unselectable="on" aria-sort="none" aria-label="X: No sort applied, activate to apply an ascending sort" style="user-select: none;"><div class="tablesorter-header-inner">X</div></th><th data-column="1" class="tablesorter-header tablesorter-headerUnSorted" tabindex="0" scope="col" role="columnheader" aria-disabled="false" unselectable="on" aria-sort="none" aria-label="Name: No sort applied, activate to apply an ascending sort" style="user-select: none;"><div class="tablesorter-header-inner">Name</div></th><th data-column="2" class="tablesorter-header tablesorter-headerUnSorted" tabindex="0" scope="col" role="columnheader" aria-disabled="false" unselectable="on" aria-sort="none" aria-label="Type: No sort applied, activate to apply an ascending sort" style="user-select: none;"><div class="tablesorter-header-inner">Type</div></th><th data-column="3" class="tablesorter-header tablesorter-headerUnSorted" tabindex="0" scope="col" role="columnheader" aria-disabled="false" unselectable="on" aria-sort="none" aria-label="Size: No sort applied, activate to apply an ascending sort" style="user-select: none;"><div class="tablesorter-header-inner">Size</div></th><th data-column="4" class="tablesorter-header tablesorter-headerUnSorted" tabindex="0" scope="col" role="columnheader" aria-disabled="false" unselectable="on" aria-sort="none" aria-label="Value: No sort applied, activate to apply an ascending sort" style="user-select: none;"><div class="tablesorter-header-inner">Value</div></th></tr></thead><tbody aria-live="polite" aria-relevant="all"><tr role="row"><td>  </td></tr></tbody></table></div></div><div class="ui-resizable-handle ui-resizable-e" style="z-index: 90;"></div><div class="ui-resizable-handle ui-resizable-s" style="z-index: 90;"></div><div class="ui-resizable-handle ui-resizable-se ui-icon ui-icon-gripsmall-diagonal-se" style="z-index: 90;"></div></div></body></html>