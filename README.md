# Staff-only-Announcements-

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>No Sweat™ Official Announcements</title>

<style>
body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: #0b1220;
    color: white;
}

header {
    background: #121a2f;
    padding: 16px;
    font-size: 26px;
    font-weight: bold;
    text-align: center;
}

.container {
    max-width: 720px;
    margin: auto;
    padding: 30px;
}

label {
    display: block;
    margin-top: 15px;
    font-weight: bold;
}

input, textarea {
    width: 100%;
    padding: 10px;
    margin-top: 5px;
    background: #10182e;
    color: white;
    border: 1px solid #2b3b66;
}

textarea {
    height: 150px;
}

button {
    margin-top: 25px;
    padding: 14px;
    width: 100%;
    background: #4da3ff;
    border: none;
    cursor: pointer;
    font-weight: bold;
    color: black;
}

button:hover {
    opacity: 0.9;
}

.note {
    margin-top: 15px;
    font-size: 14px;
    opacity: 0.8;
}
</style>
</head>

<body>

<header>No Sweat™ Official Announcements</header>

<div class="container">

<label>From (e.g. Mr Flop):</label>
<input id="from" placeholder="Mr Flop">

<label>Announcement Title:</label>
<input id="title" placeholder="Official Announcement">

<label>Announcement Description:</label>
<textarea id="description" placeholder="Type the announcement here..."></textarea>

<button onclick="sendAnnouncement()">Send Announcement</button>

<p class="note">
This will send an <strong>@everyone</strong> ping and a formatted announcement embed.
</p>

</div>

<script>
const webhookURL = "https://discord.com/api/webhooks/1455717695566909483/3tlSuMgaxR3O3724jz22nYm-7edyxqe_bP8mYuNLnBB01C2ZLQYrtTUYbv6JD8VNnRVS";

function sendAnnouncement() {
    const from = document.getElementById("from").value || "Staff Team";
    const title = document.getElementById("title").value || "Announcement";
    const description = document.getElementById("description").value || "No description provided.";
    const timestamp = new Date().toLocaleString();

    fetch(webhookURL, {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
            content: "@everyone",
            embeds: [{
                title: title,
                description: description,
                color: 3447003,
                fields: [
                    { name: "From", value: from, inline: true },
                    { name: "Sent At", value: timestamp, inline: true }
                ],
                footer: {
                    text: "✅ When you have fully read this message and acknowledge, please react."
                }
            }]
        })
    });

    alert("Announcement sent successfully.");
}
</script>

</body>
</html>
