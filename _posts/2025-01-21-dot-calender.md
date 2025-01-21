---
layout: page
title: "Dot Calender"
subtitle: "점 달력"
date: 2025-01-21 21:20:00 +0900
categories: ["general"]
---

# 365 Days Calendar

This calendar shows today's date, how many days are left in the year, and a clickable dot for each day.

<div id="info" style="margin-bottom: 20px; font-size: 1.2em; font-weight: bold;"></div>
<div id="calendar" style="display: grid; grid-template-columns: repeat(30, 1fr); gap: 5px; max-width: 90vw; margin: 20px auto;"></div>

<script>
  const today = new Date();
  const year = today.getFullYear();
  const startOfYear = new Date(year, 0, 1);
  const endOfYear = new Date(year, 11, 31);
  const dayOfYear = Math.floor((today - startOfYear) / (1000 * 60 * 60 * 24)) + 1;
  const daysLeft = Math.floor((endOfYear - today) / (1000 * 60 * 60 * 24));

  // Display today's date and days left
  const info = document.getElementById('info');
  info.textContent = `Today: ${year}/${String(today.getMonth() + 1).padStart(2, '0')}/${String(today.getDate()).padStart(2, '0')}. ${daysLeft} days left until ${year} ends.`;

  // Generate calendar dots
  const calendar = document.getElementById('calendar');
  for (let i = 1; i <= 365; i++) {
    const day = document.createElement('div');
    day.style.width = '20px';
    day.style.height = '20px';
    day.style.borderRadius = '50%';
    day.style.backgroundColor = i < dayOfYear ? 'blue' : i === dayOfYear ? 'green' : 'gray';
    day.style.cursor = 'pointer';
    day.style.transition = 'transform 0.2s';
    day.style.display = 'inline-block';
    day.style.margin = '2px';

    day.onmouseover = () => (day.style.transform = 'scale(1.2)');
    day.onmouseout = () => (day.style.transform = 'scale(1)');
    day.onclick = () => {
      alert(`You clicked on day ${i}`);
      // Uncomment to link to another page
      // window.location.href = `/day${i}.html`;
    };

    calendar.appendChild(day);
  }
</script>
