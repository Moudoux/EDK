The EMC (Easy Minecraft Client) Development Kit
===================

Development kit for [EMC](https://github.com/Moudoux/EMC)

Setting up your IDE to develop with EMC
-------------------

1. Download the [latest EMC api release](https://github.com/Moudoux/EMC/releases)
2. Make a new maven project in your favourite IDE
3. Import the EMC api jar to your project (Add it to your local maven repo, or add it as a jar)
4. You can now proceed to making your first mod.

Making your first mod with EMC
-------------------

1. Create a file called `client.json` in the root of your project, this file is used so that EMC can find your main class and info about your mod.
2. In that file add the following:

```
{

    "name":"EMC Client",
    "website":"https://github.com/Moudoux/Example-EMC-Client",
    "author":"Deftware",
    "minversion":12.8,
    "version":1,
    "main":"me.deftware.client.Main.Main",
    "updateLinkOverride": false

}
```

3. Create the main class you specified in the `client.json` file.
4. Extend your class by `EMCClient`, add the required methods.
5. Here's a example of a main class:


```
package me.deftware.client;

import me.deftware.client.framework.Client.EMCClient;
import me.deftware.client.framework.Event.Event;
import me.deftware.client.framework.Event.Events.EventClientCommand;
import me.deftware.client.framework.Wrappers.IChat;

public class Main extends EMCClient {
	
	private EMCClientInfo clientInfo;
	
	@Override
	public void initialize() {
		// Mod name, mod version
		clientInfo = new ClientInfo("Example mod", "1");
	}

	@Override
	public EMCClient getClientInfo() {
		// This is used for the framework to know what client it has
		return clientInfo;
	}

	@Override
	public void onEvent(Event event) {
		// Handle event
	}

}
```

If you want more help you can check out the [Example mod](https://github.com/Moudoux/Example-EMC-Client) made with EMC.

Packaging your mod for installation
-------------------

1. Export your mod to a jar file named `Client.jar` (Must be that name!)
2. Download the [latest EMC installer](https://github.com/Moudoux/EMC-Installer/releases)
2. Open the installer jar file, drag the `EMC.json` file to your desktop (for example)
3. Open the json file and change the client name to your client name.
4. Replace the `EMC.json` file in the installer jar with your modified json file. 
5. Create a folder called `assets`, in this folder add your `Client.jar`
6. Drag `assets` into the installer jar file.

You're done, the installer will now install your mod with EMC. Run it with `java -jar <installer_file>.jar` or double click it.

License
-------------------


EMC is licensed under GPL-3.0