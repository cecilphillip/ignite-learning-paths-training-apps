# Demos instructions

The following document describe how to do all the demos presented during the session. You must have completed the [deployment](../deployment/README.md) before attempting to do the demos.

## Suggested setup to present

> You should have a few things open and ready:

- PowerPoint at the title slide
- Browser Tab: Portal Azure Dashboard/ home
- Browser Tab: Tailwind traders website (from PaaS solution)
- Browser Tab: Scale sets Resource Group
- Browser Tab: PaaS Resource Group
- Browser Tab: Key Vault
- Visual Studio Code, with the Azure CLI to create a scale set
    ```
    az vmss create \
        -g $RGName \
        -n myScaleSet \
        --image "/subscriptions/<subscription ID>/resourceGroups/myGalleryRG/providers/Microsoft.Compute/galleries/myGallery/images/myImageDefinition/versions/1.0.0" \
        --admin-username azureuser \
        --generate-ssh-keys
   ```
- ZoomIt (or another application that zoom your screen) should be running, there is tiny stuff to show.
- Vysor with your mobile screen displayed. 

---

## Demo 1 - Let’s Create a VM 

- From Portal Azure Dashboard/ home
- Click +, and type "Virtual machine scale set", then click the button create.
- Explains a few things like the fact that you can use YOUR custom golden images...
- Magic of Ignite, you already have a scale set create.
- Switch to the Browser Tab: Scale sets Resource Group
- Explain the resources (some are missing because if a fake right now)
- Click on Virtual machine scale set
- Show the metrics (CPU, Network, etc.)
- At the top of left panel type "Scaling" in the search bar. 
    * Explain that little trick
    * Click on Scaling
- Explain how easy it is to scale MOVE THE CURSOR
- Click on the AutoScale 
- Provide some scenario scale Up by on number of item in a queue, or CPU...
- Explain that it's also very important to think about the scale down and cooldown.
- Don't save anything.

Now Let's see more details about the two VMs are suppose to have.

- Still from the scale set, click Instance from the left panel
- Here are our 2 VMS, click on one.
- Show again how that a VM like they know CPU, Memory, etc....

Let's now connect to this VM

- Click on Connect
- copy into the clipboard the `ssh username@000.000.000.000` display in the right panel.

This time to show that great extension we mention previously.

- Switch to VSCode, with the Azure CLI Code
- Mention that you showed how to create the VM and scale set using the portal but that it's of course possible to create it using ARM template or simple Azure CLI command like this one.

Let's show some Details about the Extensions in VSCode
- Open the Extension menu, type Remote to display all the remote option 

Now let's connect to the VM

- Click the lower corner of Code the **><**
- Select *Remote-SSH: Connect to Host...* option
- Paste the clipboard
- enter your passphrase

Have some fun the the VM. When it will be the real tailwind VM the app should be available from the root "/"

- Exit 
- Disconnect shh

Demo 1 is done, let's do demo 1.5.

---

## Demo 2 - Plan B: PaaS - WebApp

Now it's time to introduce the PaaS setup. Some people prefer VM other will embrace the PaaS and go VMsless

- Switch to the Browser Tab: PaaS Resource Group
- Show the different resources (avoid talking about Key vault)
- Click on App Service
- The the top panel the information available 
    * Switch to the Browser Tab: Tailwind traders website momentarily to show the website
- Show the metrics, Backup, and all other create "built-in" feature of PaaS
- At the top of left panel type "Scale" in the search bar. 
    * Explain difference between Scale Up and scale out
    * Click on scale out
- Explain how easy it is to scale MOVE THE CURSOR
- Click on the AutoScale 
- Once more quick recap of some scenario to auto-scale 
- Don't save anything.
- Open the Configuration just saying that this is you can put setting, configuration and stuff... stay brief, we will come back.

Demo 1 done. Back to slide.

---

## Demo 3 - Securing the app with Azure Key Vault

- From the portal, back to tab with the Configuration open
- Show a "old way" to do by showing the CosmoDB connection String **use the ZOOM**
- Now show the SQLConnectionString

Let's explain where it come from. See Before that talk you already created a Key Vaul. 

- Switch to Browser Tab: Key Vault
- Creating one is super simple `az keyvault create`, or a few textbox from the portal.
- Open Show the button to add secret
- From the left panel click on Secret, and click again.
- Provide information about where the URL come from, show the real connectionstring
- Explains the how you could do a ne version or the and expiration date.

--- 

## Demo 4 - Quick look at the Tailwind Traders App

- Switch to Vysor.
- Explains that this a real phone that you are mirroring to our computer so they can see.

Open the Tailwind traders application. This app was made in C# and Xamarin. It's available on iOS and Android sharing the same code, and leveraging many services in Azure as backend. If fact let's go in the Settings show I can show you the API that the application is calling...

- Click on the hamburger menu and select Settings.

So you could use the same API for your website and your application. And those component could scale depending on the demand if each services. In fact if you are interested to know more about this App in MOD30 this will show the behind the scene. I will show when and where this session is in the last slides.

But before let's try that App. How about we add some item in my wishlist. So first I will go back to the main screen. and click that big button *StartSmart Shopping by taking a photo*.

- Take a photo, or use a photo already available in the mobile device.

Now if we go in the wishlist we should see the item... see something smart about it.

- Take a few second.... Click on the hamburger menu and select wishlist.
- Found your item...

The photo was uploaded to the cloud was analyzed by some AI (aka Azure Cognitive Services) and than the description is return in my phone! How cool is that!

This is possible using Azure serverless, but I won't tell more ( teasing LOL) 

- Get back to the slide.
