const express = require("express");
const mineflayer = require('mineflayer');

const app = express();

// HTTP server عشان Render / Uptime Robot
app.get("/", (req, res) => {
  console.log("✅ Uptime Robot زار البوت!");
  res.send("Bot is alive!");
});

const listener = app.listen(process.env.PORT || 3000, () => {
  console.log(`البوت شغال على البورت ${listener.address().port}`);
});

// إنشاء البوت
const bot = mineflayer.createBot({
  host: 'LOBIXEL.aternos.me',  // غيّر هذا لعنوان سيرفرك
  port: 61097,                  // غيّر البورت إذا مختلف
  username: '3BD'               // اسم البوت اللي تريده
});

// حركات عشوائية للبوت
function randomMove() {
  const moves = ['left', 'right', 'forward', 'back'];
  const move = moves[Math.floor(Math.random() * moves.length)];
  bot.setControlState(move, true);
  setTimeout(() => bot.setControlState(move, false), 1000 + Math.random() * 2000);
}

function randomJump() {
  bot.setControlState('jump', true);
  setTimeout(() => bot.setControlState('jump', false), 500);
}

// عند دخول البوت للسيرفر
bot.on('spawn', () => {
  console.log('✅ البوت دخل السيرفر!');

  setInterval(() => {
    randomMove();
    randomJump();
  }, 5000);

  setInterval(() => {
    bot.chat('السلام عليكم! أنا بوت بسيط 🤖');
  }, 60000);
});

bot.on('kicked', console.log);
bot.on('error', console.log);
