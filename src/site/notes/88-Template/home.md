```dataviewjs
let setting = {};
let history = Object.assign(JSON.parse(await app.vault.adapter.read(".obsidian/.diary-stats")));
let today = moment().format("YYYY-MM-DD");
if (history.hasOwnProperty(today))
{let weather=history[today].weather;
let todayweather = weather[0];
setting.iconDay =  weather[0].iconDay;
setting.windSpeedDay =  weather[0].windSpeedDay;
setting.windSpeedNight =  weather[0].windSpeedNight;
await dv.view("88-Template/script/dv_weatherSvg",setting)
let desc = ` <%+ tp.date.now("A好，今天是YYYY年MM月Do dddd") %> ，${todayweather.city} ${todayweather.textDay}， ${todayweather.tempMin}~${todayweather.tempMax}℃  ${todayweather.air} ${todayweather.windydesc} [[最近天气查询|✈️]] \n云朵充盈了${todayweather.cloud}%的天空\n顺便，如果有机会看见月亮的话，那么它应该是这样的${todayweather.moonPhase.replace(/[\u4e00-\u9fa5]/g,"")}`;
dv.paragraph(desc);
}
>```