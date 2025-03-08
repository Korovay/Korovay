<p align="center">
  <img src="https://i.imgur.com/a5mJ991.png" alt="Header">
  <br>
  i see you! hehe / °〆° \
  <br>
  <a href="https://info.flagcounter.com/wugL">
    <img src="https://s05.flagcounter.com/count2/wugL/bg_FFFFFF/txt_000000/border_CCCCCC/columns_2/maxflags_10/viewers_0/labels_1/pageviews_1/flags_0/percent_0/" alt="Flag Counter" border="0">
  </a>
  <br>
  <a href="https://discord.gg/QMK6YAZ2UQ">
    <img src="https://img.shields.io/discord/1203767982157733888" alt="Discord">
  </a>
  <br>
  <div align="center">
    <img src="https://i.imgur.com/zpRmwZG.gif" width="100"/>
  </div>
  <br>
  <div align="center">
    <img src="https://i.imgur.com/yhSjWow.png" width="350"/>
  </div>
  <br>


### Build-A-Bot
```js
// Main function to fetch and update battle logs
async function fetchAndUpdateBattleLogs() {
    try {
        const response = await axiosInstance.get(`https://api.brawlstars.com/v1/clubs/%232CCCRYJYV/members`, {
            headers: { 'Authorization': `Bearer ${process.env.BRAWL_STARS_API_KEY_ClubBattleLog}` }
        });

        const clubMembers = response.data.items;
        const currentTags = new Set(clubMembers.map(user => user.tag));

        const existingLogs = await ClubBattleLog.find();
        await processExitedUsers(existingLogs, currentTags);

        if (isSeasonEnded()) {
            SEASON_END_DATE = moment.tz('Europe/Kyiv').startOf('day').add(SEASON_DURATION_DAYS, 'days').hour(12);
            console.log(`Season has ended, new end date: ${SEASON_END_DATE.toISOString()}`);
        }

        const userPromises = clubMembers.map(async (user) => {
            const brawlStarsTag = user.tag.startsWith('#') ? user.tag.substring(1) : user.tag;

            try {
                const [playerResponse, battleLogResponse] = await Promise.all([
                    axiosInstance.get(`https://api.brawlstars.com/v1/players/%23${brawlStarsTag}`, {
                        headers: { Authorization: `Bearer ${process.env.BRAWL_STARS_API_KEY_ClubBattleLog}` }
                    }),
                    axiosInstance.get(`https://api.brawlstars.com/v1/players/%23${brawlStarsTag}/battlelog`, {
                        headers: { Authorization: `Bearer ${process.env.BRAWL_STARS_API_KEY_ClubBattleLog}` }
                    })
                ]);
```


  <div align="center">
    <img src="https://i.imgur.com/UhXU5rb.png" width="350"/>
  </div>
</p>
