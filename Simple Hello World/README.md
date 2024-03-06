# Simple Hello World
This is just a template project, basically. Supports both Pale Moon and Basilisk out of the box.

Why is it Undertale themed? There's someone I know who will be very pissed about it.

To use this yourself, first you need to change the data in `install.rdf`, for example: 

install.rdf
```
<RDF xmlns="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
	xmlns:em="http://www.mozilla.org/2004/em-rdf#">
	<Description about="urn:mozilla:install-manifest"
			em:id="my-extension@mydomain.com" em:version="1.0" em:name="My Extension"
			em:description="My brilliant XUL extension"
			em:creator="Me!" 
			em:iconURL="chrome://my-extension/skin/icon256.png"
			em:icon64URL="chrome://my-extension/skin/icon64.png"
			em:homepageURL="https://mydomain.com/my-extension"
			em:unpack="false" em:type="2">
		<em:targetApplication name="Basilisk">
			<Description
				em:id="{ec8030f7-c20a-464f-9b0e-13a3a9e97384}" em:minVersion="52.0"
				em:maxVersion="52.*" />
		</em:targetApplication>
		<em:targetApplication name="Pale Moon">
			<Description
				em:id="{8de7fcbb-c55c-4fbe-bfc5-fc555c87dbc4}" em:minVersion="28.0.0a1" 
				em:maxVersion="33.*" />
		</em:targetApplication>
	</Description>
</RDF>
```

You should then change the values in `Makefile` to match your new extension-to-be.

Then you have to point `chrome.manifest` to your ID (change all instances of "hoi" to whatever your extension ID is), because this is what UXP uses to load your overlays.

Then you need to modify the files in the content directory (If you just want a simple icon, it's already set up for you).

Lastly, change the data in the skin directory, including browserOverlay.css. (Would be a shame if it didn't actually load your icons.)

To build your new extension, simply `cd` into the directory your extension is in, and just run `make`.

Your new extension should be dumped into the `bin` folder, ready to install!
(You should also set up some testing profiles for your extension to make development easier, but you can comment those out of the makefile if you really don't want them.)
