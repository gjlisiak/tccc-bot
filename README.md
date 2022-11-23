# Tactical Combat Casualty Care (TCCC) Bot

## Project Description
The Tactical Combat Casualty Care (TCCC) bot brings together the Stop the Bleed protocol and the TCCC Guidelines as an easy-to-use field training and field triage support tool.  While the Care Under Fire, Tactical Field Care (TFC) and Tactical Evacuation Care (TACEVAC) components are geared towards trained professionals, the TCCC bot includes the Stop the Bleed protocol which is geared towards anyone.

The TCCC bot was developed and delivered at the direction and request of an international NGO. 

## Development and Deployment Resources

### Azure Health Bot

This project is comprised of 23 scenarios which have been logically organized and grouped through the use of menus. Users can navigate the Tactical Field Care and Tactical Evacuation Care scenarios in a stepwise fashion, or they can go directly to the necessary components.

### Adaptive Cards

The TCCC bot makes heavy use of Adaptive Cards for delivering the chat experience.  These adaptive cards display images, videos, audios, and icons as needed during scenario execution.  The icons are used to help identify steps that are specific to Combat Medics and Combat Paramedics as defined by the TCCC guidelines.  The links for the images, videos, and audio files are defined as conversation level variables in the "main menu" scenario and used throughout nearly every scenario. 

### Storage Containers

Images, videos, audios, and icon files need to be stored in an accessible resource location.  This can be done within the App Service itself or centrally in Azure Storage containers.  Irrespective of the path chosen, an environment variable is used to point to the centrally accessible resource location.

### Web Container Deployment

The Health Bot Container sample [Git Repo](https://github.com/microsoft/HealthBotContainerSample/) is an easy to deploy means of providing the web front-end for the TCCC bot.  Once deployed, parameters can be appended to the end of the URL to trigger multi-language support.

- `Auto Detect` "/?locale=autodetect"
- `English override` "/?locale=en-us"
- `Ukrainian` "/?locale=uk-ua"

### Environment Variables

The bot requires the use of two environment variables. The first is used for displaying the local emergency telephone number allowing bot users on mobile devices to initiate the emergency phone call right from the bot.  The second environment variable is the root location of the image, video, and audio files.  The bot will function without a resource location being specified, but the adaptive cards will display improperly.
 
- `help_emergency` number for emergency services (e.g., 911)
- `resourceLoc` the root location for the storage containers

### Multi-Language Support

The TCCC bot was developed in a highly scalable fashion and translated into Ukrainian at the request of the NGO.  Additional languages can be added easily via updates to Excel which would be subsequently uploaded to the Azure Health Bot.  The only remaining effort required to fully support additional languages is to update the Global Resources action block in the main menu scenario.  This is critical if you intend to incorporate language specific images, audios, or videos.

## Project Resources and References

### Stepwise Scenario Execution Flow

The bot was developed to support stepwise execution of the TFC or TACEVAC protocols.  Alternatively, the various menu scenarios will allow for direct access to the condition or situation specific resources.

### TCCC Guidelines Resources & Adaptations

The logic for the Care Under Fire, TFC and TACEVAC scenarios are based on the decision flow diagrams contained in the Tactical Combat Casualty Care Quick Reference Guide, First Edition, 2017 (C).  Scenario logic was made based on the subsequent update releases at the direction of the requesting NGO for which this TCCC bot was delivered.  Additional information can be found on the [Joint Trauma System](https://jts.health.mil/index.cfm/committees/cotccc) website.

### Stop the Bleed Resource and Adaptations

The Stop the Bleed scenario was adapted from the American College of Surgeons' [Stop the Bleed](https://www.stopthebleed.org/) protocols including decision logic derived from [Hartford Consensus Zones of Care](https://www.stopthebleed.org/resources-poster-booklet/compressing-zones/).

