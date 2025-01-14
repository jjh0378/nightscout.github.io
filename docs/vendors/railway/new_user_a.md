---
orphan: true
---

# </br>

a) Click on `Create a New project`.

<img src="/vendors/railway/img/Railway06.png" width="400px" /></br>

If you don't see that, top right, click `+ New Project`.

<img src="/vendors/railway/img/RailwayDB01.png" width="200px" /></br>

</br>

b) Select `Deploy from GitHub repo`.

<img src="/vendors/railway/img/RailwayM19.png" width="400px" /></br>

</br>

c) Select `Configure GitHub App`.

<img src="/vendors/railway/img/RailwayM02.png" width="400px" /></br>

</br>

d) Choose `Only select repositories`, in the `Select repositories` drop-down select your own fork of `cgm-remote-monitor`.  
Then, at the bottom, click `Install & Authorize`.

<img src="/vendors/railway/img/Railway08.png" width="400px" /></br>

</br>

e) You should be back to `Deploy from GitHub repo`, select it.

<img src="/vendors/railway/img/RailwayM19.png" width="400px" /></br>

</br>

f) Now you can select your own GitHub repository.

<img src="/vendors/railway/img/RailwayM03.png" width="400px" /></br>

</br>

g) Select `Add variables`.

<img src="/vendors/railway/img/RailwayM20.png" width="400px" /></br>

</br>

h) The Nightscout project will deploy in the background, just ignore it: now we need to setup our Nightscout variables.  
Click on `Raw Editor`.

<img src="/vendors/railway/img/RailwayM21b.png" width="700px" /></br>

The raw editor will open, leave it like this for now.

<img src="/vendors/railway/img/RailwayM21c.png" width="500px" /></br>

</br>

i) Compile the information below.

File all necessary fields, click on the Validate button at the bottom of the form, if no error is seen you will have all variables displayed in the text box at the bottom, click on the Copy All button.

<img src="/vendors/railway/img/Railway42.png" width="600px" /></br>

#### Mandatory variables

These three variables below must have a value.

**MONGODB_URI**

The MongoDB Connection String to connect to your MongoDB cluster. If you don't have this from your Mongo database, please re-read installation instructions at [Nightscout database](https://nightscout.github.io/nightscout/database) before continuing

<input type="text" id="MONGODB_URI" value="" size="100"></br>

**API_SECRET**

<input type="text" id="API_SECRET" value="" size="40"></br>

A passphrase that must be at least 12 characters long. Avoid special characters, which can cause problems in some cases

**DISPLAY_UNITS**

<select id="DISPLAY_UNITS">
    <option value="MGDL" selected="selected">mg/dl</option>
	<option value="MMOL">mmol/l</option></select></br>
</br>Preferred BG units for the site: `mg/dl` or `mmol/l` (or just `mmol`)

</br>

#### Customizations

Leave default values if you don't want to change them

**CUSTOM_TITLE**

<input type=text id=CUSTOM_TITLE value="Nightscout" size=40></br>

The display name for the Nightscout site. Appears in the upper left of the main view. Often set to the name of the CGM wearer

**THEME**

<select id="THEME">
      <option value="COLORS" selected="selected">colors</option>
      <option value="DEFAULT">default</option>
      <option value="COLORBLINDFRIENDLY">colorblindfriendly</option></select></br>
</br>Default setting for new browser views for the color theme of the CGM graph. (`default` `colors` or `colorblindfriendly`)

**ENABLE**

<input type=text id=ENABLE value="careportal basal dbsize rawbg iob maker cob bwp cage iage sage boluscalc pushover treatmentnotify loop pump profile food openaps bage alexa override speech cors" size=100></br>

Plugins to enable for your site. Must be a space-delimited lower-case list. Include the word `bridge` here if you are receiving data from the Dexcom Share service

**SHOW_PLUGINS**

<input type=text id=SHOW_PLUGINS value="careportal dbsize" size=100></br>

Default setting for whether or not these plugins are checked (active) by default not merely enabled. Include plugins here as in the ENABLE line; space-separated and lower-case

**TIME_FORMAT**

<select id="TIME_FORMAT">
        <option value="TWELVE" selected="selected">12</option>
        <option value="TWENTYFOUR">24</option></select></br>
</br>Default setting for new browser views for the time mode. (`12` or `24`)

**NIGHT_MODE**

<select id="NIGHT_MODE">
        <option value="OFF" selected="selected">off</option>
    <option value="ON">on</option></select></br>
</br>Default setting for new browser views for whether Night Mode should be enabled. (`on` or `off`)

**BOLUS_RENDER_OVER**

<input type=text id=BOLUS_RENDER_OVER value="1" size=10></br>

U value over which the bolus values are rendered on the chart if the `x U and Over` option is selected

</br>

#### Dexcom Share

If you want Nightscout to import directly from Dexcom Share

**BRIDGE_USER_NAME**

 <input type=text id=BRIDGE_USER_NAME value="" size=40></br>

Your Dexcom account username to receive CGM data from the Dexcom Share service. Also make sure to include `bridge` in your ENABLE line.

**BRIDGE_PASSWORD**

<input type=text id=BRIDGE_PASSWORD value="" size=40></br>

Your Dexcom account password to receive CGM data from the Dexcom Share service. Also make sure to include `bridge` in your ENABLE line

**BRIDGE_SERVER**

<select id="BRIDGE_SERVER">
    <option value="US" selected="selected">US</option>
    <option value="EU">EU</option></select></br>
</br>If you are bridging from the Dexcom Share service and are anywhere *outside* the US change this to EU. (`US` or `EU`)

</br>

#### Alarms

You can customize alarms or leave them to default values

**ALARM_TYPES**

<select id="ALARM_TYPES">
    <option value="SIMPLE" selected="selected">simple</option>
    <option value="PREDICT">predict</option>
    <option value="SIMPLEPREDICT">simple predict</option></select></br>
</br>`simple` and/or `predict`v. Simple alarms trigger when BG crosses the various thresholds set below. Predict alarms use a formula that forecasts where the BG is going based on its trend. You will *not* get warnings when crossing the BG thresholds set below when using the predict type

**ALARM_URGENT_HIGH**

<select id="ALARM_URGENT_HIGH">
    <option value="ON" selected="selected">on</option>
    <option value="OFF">off</option></br>
</br>Default setting for new browser views for the Urgent High alarm (triggered when BG crosses BG_HIGH). (`on` or `off`)

**BG_HIGH**

<input type=text id=BG_HIGH value="260" size=20></br>

Urgent High BG threshold triggers the `ALARM_URGENT_HIGH` alarm. Set in mg/dL or mmol/L as set in `DISPLAY_UNITS` variable

**ALARM_URGENT_LOW**

<select id="ALARM_URGENT_LOW">
    <option value="ON" selected="selected">on</option>
    <option value="OFF">off</option></br>
</br>Default setting for new browser views for the Urgent Low alarm (triggered when BG crosses `BG_LOW`). (`on` or `off`)

**BG_LOW**

<input type=text id=BG_LOW value="55" size=20></br>

Urgent Low BG threshold triggers the `ALARM_URGENT_LOW` alarm. Set in mg/dL or mmol/L as set in `DISPLAY_UNITS` variable

**ALARM_HIGH**

<select id="ALARM_HIGH">
    <option value="ON" selected="selected">on</option>
    <option value="OFF">off</option></br>
</br>Default setting for new browser views for the High alarm (triggered when BG crosses `BG_TARGET_TOP`). (`on` or `off`)

**BG_TARGET_TOP**

<input type=text id=BG_TARGET_TOP value="180" size=20></br>

High BG threshold triggers the `ALARM_HIGH` alarm. Set in mg/dL or mmol/L as set in `DISPLAY_UNITS` variable

**ALARM_LOW**

<select id="ALARM_LOW">
    <option value="ON" selected="selected">on</option>
    <option value="OFF">off</option></br>
</br>Default setting for new browser views for the Low alarm (triggered when BG crosses `BG_TARGET_BOTTOM`). (`on` or `off`)

**BG_TARGET_BOTTOM**

<input type=text id=BG_TARGET_BOTTOM value="70" size=20></br>

Low BG threshold triggers the `ALARM_LOW` alarm. Set in mg/dL or mmol/L as set in `DISPLAY_UNITS` variable

**ALARM_TIMEAGO_URGENT**

<select id="ALARM_TIMEAGO_URGENT">
    <option value="ON" selected="selected">on</option>
    <option value="OFF">off</option></br>
</br>Default setting for new browser views for an urgent alarm when CGM data hasn't been received in the number of minutes set in `ALARM_TIMEAGO_URGENT_MINS`. (`on` or `off`)

**ALARM_TIMEAGO_URGENT_MINS**

<input type=text id=ALARM_TIMEAGO_URGENT_MINS value="30" size=20></br>

Default setting for new browser views for the number of minutes since the last CGM reading to trigger an `ALARM_TIMEAGO_URGENT` alarm

**ALARM_TIMEAGO_WARN**

<select id="ALARM_TIMEAGO_WARN">
    <option value="ON" selected="selected">on</option>
    <option value="OFF">off</option></br>
</br>Default setting for new browser views for a warning alarm when CGM data hasn't been received in the number of minutes set in `ALARM_TIMEAGO_WARN_MINS`. (`on` or `off`)

**ALARM_TIMEAGO_WARN_MINS**

<input type=text id=ALARM_TIMEAGO_WARN_MINS value="15" size=20></br>

Default setting for new browser views for the number of minutes since the last CGM reading to trigger an `ALARM_TIMEAGO_WARN` alarm

<script>
function Validate()
{
  var s, e1, e2, e3;
  e1 = "";
  e2 = "";
  e3 = "";
  s = document.getElementById("MONGODB_URI").value;
  if(s.search("mongodb")==-1) { e1 = "Bad MONGODB_URI: it should be a mongodb connection string."}
  else if(s.search("://")==-1) { e1 = "Bad MONGODB_URI: it should be a mongodb connection string."}
  else if(s.search(" ")!=-1) {e1 = "MONGODB_URI should not contain spaces."}
  else if(s.search("<")!=-1) {e1 = "MONGODB_URI should not contain < or > characters."}
  else if(s.search(">")!=-1) {e1 = "MONGODB_URI should not contain < or > characters."}
  else if(s.indexOf("@")!=s.lastIndexOf("@")) {e1 = "Do not use the character @ in your MONGODB_URI password or user name."};
  document.getElementById("result1").innerHTML = e1;
  s = document.getElementById("API_SECRET").value;
  if(s.search("@")!=-1) { e2 = "Problematic API_SECRET: do not use special characters."}
  else if(s.search(":")!=-1) { e2 = "Problematic API_SECRET: do not use special characters."}
  else if(s.search("/")!=-1) { e2 = "Problematic API_SECRET: do not use special characters."}
  else if(s.search(" ")!=-1) { e2 = "Bad API_SECRET: do not use spaces."}
  else if(s.length<12) { e2 = "Bad API_SECRET: too short - minimum 12 characters."}
  document.getElementById("result2").innerHTML = e2;
  s = document.getElementById("BRIDGE_USER_NAME").value;
  if(s.length) { s = document.getElementById("BRIDGE_PASSWORD").value;
  if(s.length) { s = document.getElementById("ENABLE").value;
  if(s.search("bridge")==-1) { e3 = "Add bridge in ENABLE to get values from Dexcom Share." } } }
  s = document.getElementById("BRIDGE_USER_NAME").value;
  if(!s.length) { s = document.getElementById("BRIDGE_PASSWORD").value;
  if(!s.length) { s = document.getElementById("ENABLE").value;
  if(s.search("bridge")!=-1) { e3 = "Remove bridge from ENABLE if you don't use Dexcom Share directly to Nightscout." } } }
  document.getElementById("result3").innerHTML = e3;
  if((e1.length + e2.length + e3.length)<1)
  {
    document.getElementById("result1").innerHTML = "Validation is PASS.";
    document.getElementById("result3").innerHTML = "Click on the Copy All button below. Go back into Railway raw editor, ENV and paste.";
    CopyAll();
  }
};
function CopyAll()
{
  var sBuffer, sLine, sel;
  sBuffer = "";
  sel = document.getElementById("ALARM_HIGH");
  sLine = "ALARM_HIGH=" + sel.options[sel.selectedIndex].text; sBuffer = sBuffer + sLine;
  sBuffer = sLine + "\n";
sel = document.getElementById("ALARM_LOW");
  sLine = "ALARM_LOW=" + sel.options[sel.selectedIndex].text; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sel = document.getElementById("ALARM_TIMEAGO_URGENT");
  sLine = "ALARM_TIMEAGO_URGENT=" + sel.options[sel.selectedIndex].text; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sel = document.getElementById("ALARM_TYPES");
  sLine = "ALARM_TYPES=" + sel.options[sel.selectedIndex].text; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sel = document.getElementById("ALARM_TIMEAGO_WARN");
  sLine = "ALARM_TIMEAGO_WARN=" + sel.options[sel.selectedIndex].text; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sel = document.getElementById("ALARM_URGENT_HIGH");
  sLine = "ALARM_URGENT_HIGH=" + sel.options[sel.selectedIndex].text; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sel = document.getElementById("ALARM_URGENT_LOW");
  sLine = "ALARM_URGENT_LOW=" + sel.options[sel.selectedIndex].text; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sel = document.getElementById("BRIDGE_SERVER");
  sLine = "BRIDGE_SERVER=" + sel.options[sel.selectedIndex].text; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sel = document.getElementById("DISPLAY_UNITS");
  sLine = "DISPLAY_UNITS=" + sel.options[sel.selectedIndex].text; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sel = document.getElementById("NIGHT_MODE");
  sLine = "NIGHT_MODE=" + sel.options[sel.selectedIndex].text; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sel = document.getElementById("THEME");
  sLine = "THEME=" + sel.options[sel.selectedIndex].text; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sel = document.getElementById("TIME_FORMAT");
  sLine = "TIME_FORMAT=" + sel.options[sel.selectedIndex].text; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sLine = "ALARM_TIMEAGO_URGENT_MINS=" + document.getElementById("ALARM_TIMEAGO_URGENT_MINS").value; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sLine = "ALARM_TIMEAGO_WARN_MINS=" + document.getElementById("ALARM_TIMEAGO_WARN_MINS").value; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sLine = "API_SECRET=" + document.getElementById("API_SECRET").value; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sLine = "BG_HIGH=" + document.getElementById("BG_HIGH").value; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sLine = "BG_LOW=" + document.getElementById("BG_LOW").value; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sLine = "BG_TARGET_BOTTOM=" + document.getElementById("BG_TARGET_BOTTOM").value; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sLine = "BG_TARGET_TOP=" + document.getElementById("BG_TARGET_TOP").value; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sLine = "BOLUS_RENDER_OVER=" + document.getElementById("BOLUS_RENDER_OVER").value; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sLine = "BRIDGE_PASSWORD=" + document.getElementById("BRIDGE_PASSWORD").value; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sLine = "BRIDGE_USER_NAME=" + document.getElementById("BRIDGE_USER_NAME").value; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sLine = "CUSTOM_TITLE=" + document.getElementById("CUSTOM_TITLE").value; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sLine = "ENABLE=" + document.getElementById("ENABLE").value; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sLine = "MONGODB_URI=" + document.getElementById("MONGODB_URI").value; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
sLine = "SHOW_PLUGINS=" + document.getElementById("SHOW_PLUGINS").value; sBuffer = sBuffer + sLine;
  sBuffer = sBuffer + "\n";
  document.getElementById("NSVARS").innerHTML = sBuffer;
};
function CopyToClipboard() {
  var copyText = document.getElementById("NSVARS");
  copyText.select();
  copyText.setSelectionRange(0, 99999); // For mobile devices
  navigator.clipboard.writeText(copyText.value);
   alert("Variables copied, now paste them in Railway Raw Editor.");
}
</script>

Now click on the Validate button below

  <button onclick="Validate()">-> Validate</button>

If errors show up below, please correct them and click Validate again.

<p id="result1">Click the button above.</p>
<p id="result2"></p>
<p id="result3"></p>

</br></br>
<button onclick="CopyToClipboard()">Copy All</button>
</br></br>

<textarea id="NSVARS" name="NSVARS" rows="27" cols="100">
Once validated you will see all Railway Nightscout variables in this box.
</textarea></br>

</br>

j)  Return to the Railway Raw editor. Paste the result. Click `Update Variables`.

<img src="/vendors/railway/img/Railway43.png" width="500px" /></br>

Your site will redeploy, wait until redeploy completes.