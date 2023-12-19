# bitsxlaMarato live page

[![Netlify Status](https://api.netlify.com/api/v1/badges/71c013e3-dd84-4bc9-b55e-548fd0b8666d/deploy-status)](https://app.netlify.com/sites/bits-live-2020/deploys) 

> This repository contains the live page for Bits x la Marato. Devloped by Hackers@UPC in Vue.js.

# How to develop or update the live page

> To be able to install this project is necessary to run it in a node specific version. So for that you need to have installed Node.js

## Install and run the project

### Install the correct version of Node and install it

1. Have NVM installed in you system, if you don't have it, [install it](https://github.com/nvm-sh/nvm/blob/master/README.md)
2. Install the expected version in nvm we will use:
    ```sh
   nvm install 12.22.12
   ```
3. Change the current version to the one that we just installed:
    ```sh
   nvm use 12.22.12
   ```

### Clone the project

```sh
git clone https://github.com/BitsxlaMarato/bits-live.git
cd bits-live
```

### Install the dependencies of project

   ```sh
    npm install
   ```

_If you are having any problem when installing dependencies, check the Troubleshooting guide_

### Run the project

Use `npm run serve` to compile and serve the dist directory in real time. Then view the website at [https://localhost:8080](https://localhost:8080)

```sh
npm run serve
```
All the changes will be reflected real time, in the browser.

## Edit content

### Change metadata

- Change in the `src/config.js` the property `notificationTitle` setting the correct year.
- Change in the `public/index.html` the following properties:
  - `<title>` setting the correct year (line 8).
  - `<meta property="og:title">` setting the correct year (line 35).


### Change theme

If you want to change the theme you should change some properties
1. For changing the background image: Go to `public/assets/live/bg.jpg` and replace it with the one you want (with the same name).
2. For changing all the colors: Go to `src/live/params.scss` and in the top of the file you will find all the colors.

### Update basic information

The screens you will need to change for sure, are the following ones:

#### Home page (Inici)

1. Change the password Wi-Fi in `src/views/components/Home.vue`. In the `line 10 and 11` you will find the SSID and the password
2. Change the **Devpost** link in `src/views/components/Home.vue`. In the `line 20` you will find the link.
3. Change the **Slack** link in `src/views/components/Home.vue`. In the `line 29` you will find the link and the title.

If needed change the social media links also, adding, removing or changing the links in `src/live/components/Home.vue` in the blocks starting in the `line 35 to 46` and `line 47 to 55`.

#### Donations (Donatius)

Change the link to redirect to the donations page, you can change in `src/views/App.vue`. In `lines 32 and 63` you will find the links.

#### Challenges (Reptes)

Change all the challenges in `src/views/components/Challenges.vue`

#### Activities (Activitats)

Change all the activities in `src/views/components/Activities.vue`

#### Schedule (Horari)

To update or change the schedule go to `public/data/schedule.json`. And you will need to do the following changes:
1. Change the start of the hackathon, this is the property `countdownStart`, the specified hour should be the start of the codding time and not the start where the events start. This will trigger the countdown to start working.
2. Add all the events in the property `days`. Each day have the following properties:
   ```json
   {
      "name": "Day of the week, example: Divendres",
      "date": "DD/MM/YYYY, example: 16/12/2023",
      "events": []
   }
   ```
   
   Each day will have events, as many as we want, inside the array of `events`. This should have the following properties:
   ```json
   {
      "id": "0",
      "title": "Registre",
      "startHour": "17:00",
      "endHour": "18:00",
      "localization": "Entrada de la sala d'actes de l'edifici Vèrtex",
      "description": "Short description"
   }
   ```
   **Note**: The `id` should be increasing in each event, 

The duration of it must be changed in `src/config.js`, and it's set in hours.

##### Schedule file

- `id` can be whatever you want, but all ids must be different
- When writing hours, prepend zeroes: Nice: 01:00; Not-so-nice: 1:00.
- Events should be ordered by starting hour
- `baseTimeOffset` should be the same output as executing (new Date()).getTimezoneOffset() in a machine with local time. (UTC - localtime in minutes)
- `dates` are DD/MM/YYYY format

> If an event doesn't have endHour, then will show only startHour, and it will finish at the same time as it starts.  
Useful to specify events that don't have concept of length or that span through more than one day ("Event start", "Event end")



## Deploy

### Deploy to localhost

Use `npm run build` to compile all dist directory. The files will be compiled to `/dist/`.

Use `serve -s dist` to just serve `/dist` at [https://localhost:5000](https://localhost:5000).

```sh
npm run build
serve -s dist
```

### Deploy to production

**Push to master**. [Netlify](https://app.netlify.com/sites/bits-live-2020) will build and deploy automatically.

If you push something that doesn't build, don't worry, it won't be published.


---

# Structure 

## Live

Features included

- Optional subscription to events - 5 minutes before notifications
- Schedule live reload
- Fancy schedule with time padding
- Normal tabular schedule
- Countdown
- Full-screen mode by pressing `p`

## Site Sections

All the sections this live page includes:

- **Home**: Important information to know during the event.
- **Live**: live realoading schedule.
- **Schedule**: All information of the schedule (title, description and time of all the activities happening).
- **Donation**: Goes into another webpage.
- **Discord**: All the information the hacker needs to know about the discord server.
- **Challenges**: Challenges proposed for the hackathons (link to the opening explanation of the challenge).
- **Activities**: All the information about the activities that will take place during the event.
- **Rules**: Hackathon rules.
- **FAQ**: All the questions and answers the hackers may have during the event.
- **Judging**: Judging criteria the hackers needs to know to develop their project.

### Config

Some parameters (offsets, timeouts, defaults) can be changed in `src/config.js`. Keep in mind that some values are just constants and should not be changed.
Here you can edit the `FAKE_DATE` parameter to test funtionalities.

## Support

If you need help understanding something of this repo you can ask the previous developers, and the Hackers@UPC webdev team.

## License

MIT © Hackers@UPC
