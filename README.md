```javascript
function dailyLog224() {
  const campaigns = [
    { name: "Welcome Email", sent: 1000, opened: 720, clicked: 180 },
    { name: "Weekly Newsletter", sent: 1500, opened: 900, clicked: 225 },
    { name: "Product Launch", sent: 2000, opened: 1300, clicked: 520 },
    { name: "Special Offer", sent: 1200, opened: 840, clicked: 336 },
    { name: "Customer Update", sent: 800, opened: 400, clicked: 80 },
  ];

  const analyzed = campaigns.map(campaign => ({
    ...campaign,
    openRate: (campaign.opened / campaign.sent) * 100,
    clickRate: (campaign.clicked / campaign.sent) * 100,
  }));

  const totalSent = campaigns.reduce(
    (sum, campaign) => sum + campaign.sent,
    0
  );

  const totalOpened = campaigns.reduce(
    (sum, campaign) => sum + campaign.opened,
    0
  );

  const totalClicked = campaigns.reduce(
    (sum, campaign) => sum + campaign.clicked,
    0
  );

  const bestCampaign = analyzed.reduce((best, current) =>
    current.clickRate > best.clickRate ? current : best
  );

  console.log("=== Email Campaign Report ===");
  console.log(`Emails Sent: ${totalSent}`);
  console.log(`Open Rate: ${(totalOpened / totalSent * 100).toFixed(2)}%`);
  console.log(`Click Rate: ${(totalClicked / totalSent * 100).toFixed(2)}%`);

  console.log("\n=== Campaign Performance ===");

  analyzed.forEach(campaign => {
    console.log(
      `${campaign.name}: Open ${campaign.openRate.toFixed(1)}%, ` +
      `Click ${campaign.clickRate.toFixed(1)}%`
    );
  });

  console.log(`\n🏆 Best Campaign: ${bestCampaign.name}`);
}

dailyLog224();
```
