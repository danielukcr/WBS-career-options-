<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Westbrook Secondary School — Staff Application</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
    * { margin: 0; padding: 0; box-sizing: border-box; font-family: system-ui, sans-serif; }
    body {
        background: #0f0f10; color: white;
        display: flex; justify-content: center; align-items: center;
        min-height: 100vh; padding: 20px;
    }
    .container {
        display: flex; background: #18181b; border-radius: 18px;
        overflow: hidden; max-width: 900px; width: 100%;
        box-shadow: 0 18px 40px rgba(0,0,0,0.6);
    }
    .sidebar {
        background: radial-gradient(circle at top left, #ff0050, #000);
        padding: 30px; min-width: 180px;
        display: flex; justify-content: center; align-items: center;
    }
    .sidebar img { width: 120px; }
    .content { padding: 30px; flex: 1; animation: fadeIn 0.5s ease; }
    h1 { font-size: 1.7rem; margin-bottom: 10px; }
    p { color: #c9c9c9; margin-bottom: 15px; line-height: 1.4; }
    .form-group { margin-bottom: 18px; }
    label { display: block; margin-bottom: 6px; font-size: 0.95rem; }
    input, textarea, select {
        width: 100%; padding: 10px; border-radius: 10px;
        border: 1px solid #27272a; background: #09090b;
        color: white; font-size: 0.9rem;
    }
    textarea { min-height: 90px; resize: vertical; }
    button {
        background: linear-gradient(135deg, #ff0050, #ff2e93);
        border: none; padding: 12px 22px; border-radius: 999px;
        color: white; font-weight: 600; cursor: pointer;
        margin-top: 10px; float: right;
    }
    .hidden { display: none; }
    .fade-out { animation: fadeOut 0.6s forwards; }
    @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
    @keyframes fadeOut { from { opacity: 1; } to { opacity: 0; } }
    .thankyou { text-align: center; padding: 40px; animation: fadeIn 1s ease; }
</style>
</head>
<body>

<div class="container">

    <div class="sidebar">
        <img src="https://media.discordapp.net/attachments/1478880251714080961/1480344311491989537/Screenshot_2026-03-07_203727-removebg-preview.png" alt="Icon">
    </div>

    <div class="content">

        <!-- PAGE 1 -->
        <div id="page1">
            <h1>Westbrook Secondary School — Staff Application Form</h1>
            <p>
                Welcome to the Westbrook Secondary School staff application process!  
                We’re excited that you’re interested in joining our dedicated team.
            </p>
            <p>
                Applicants must be at least 13 years old, have prior experience, maintain a positive reputation, and use proper grammar with at least three sentences per answer.
            </p>
            <button onclick="nextPage(1)">Next</button>
        </div>

        <!-- PAGE 2 -->
        <div id="page2" class="hidden">
            <h1>Terms & Conditions</h1>
            <p>
                By applying, you agree to provide honest information.  
                Rewards such as Robux or perks are based on performance and activity.  
                Internal information must remain private unless permission is given.
            </p>

            <div class="form-group">
                <label><input type="checkbox" id="agreeBox"> I agree to the Terms & Conditions</label>
            </div>

            <button onclick="nextPage(2)">Next</button>
        </div>

        <!-- PAGE 3 -->
        <div id="page3" class="hidden">
            <h1>Applicant Information</h1>

            <div class="form-group">
                <label>Roblox Username</label>
                <input id="robloxUser">
            </div>

            <div class="form-group">
                <label>Discord Username</label>
                <input id="discordUser">
            </div>

            <div class="form-group">
                <label>Full Roleplay Name</label>
                <input id="rpName">
            </div>

            <div class="form-group">
                <label>What are you applying for?</label>
                <select id="department">
                    <option disabled selected>Select a department</option>
                    <option>Maths Teacher</option>
                    <option>English Teacher</option>
                    <option>Science Teacher</option>
                    <option>Cover Staff</option>
                    <option>Behavioural Officer</option>
                    <option>Student Welfare Officer</option>
                </select>
            </div>

            <button onclick="nextPage(3)">Next</button>
        </div>

        <!-- PAGE 4 -->
        <div id="page4" class="hidden">
            <h1>Application Questions</h1>

            <div class="form-group">
                <label>Why have you decided to apply for staff here?</label>
                <textarea id="q1"></textarea>
            </div>

            <div class="form-group">
                <label>Please state your previous experience.</label>
                <textarea id="q2"></textarea>
            </div>

            <div class="form-group">
                <label>What qualities make a good staff member?</label>
                <textarea id="q3"></textarea>
            </div>

            <div class="form-group">
                <label>Describe your ability to work well with others.</label>
                <textarea id="q4"></textarea>
            </div>

            <button onclick="submitApplication()">Submit Application</button>
        </div>

        <!-- THANK YOU PAGE -->
        <div id="thankyou" class="hidden thankyou">
            <h1>Thank you for applying!</h1>
            <p>
                We read all applications daily.  
                If accepted or denied, you will be added to a ticket and given your result.  
                Successful applicants will proceed to an initial training course.
            </p>
            <p>Signed // Westbrook Secondary’s Senior Leadership Team</p>
        </div>

    </div>
</div>

<script>
function nextPage(page) {
    if (page === 2 && !document.getElementById("agreeBox").checked) {
        alert("You must agree to the Terms & Conditions before continuing.");
        return;
    }
    document.getElementById("page" + page).classList.add("hidden");
    document.getElementById("page" + (page + 1)).classList.remove("hidden");
}

async function submitApplication() {

    const webhook = "https://discord.com/api/webhooks/1480768368087929086/Y3d7oYPZxqbpX-JkzdY80SGO50kX-ysnegZk7OBJpFJJ56x1wbnn3xq083eUR428TOGQ";

    const data = {
        embeds: [
            {
                title: "📘 New Staff Application Submitted",
                color: 3447003,
                fields: [
                    { name: "Roblox Username", value: document.getElementById("robloxUser").value || "N/A" },
                    { name: "Discord Username", value: document.getElementById("discordUser").value || "N/A" },
                    { name: "Roleplay Name", value: document.getElementById("rpName").value || "N/A" },
                    { name: "Department Applied For", value: document.getElementById("department").value || "N/A" },
                    { name: "Why Apply?", value: document.getElementById("q1").value || "N/A" },
                    { name: "Previous Experience", value: document.getElementById("q2").value || "N/A" },
                    { name: "Qualities", value: document.getElementById("q3").value || "N/A" },
                    { name: "Teamwork & Communication", value: document.getElementById("q4").value || "N/A" }
                ],
                timestamp: new Date().toISOString()
            }
        ]
    };

    await fetch(webhook, {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(data)
    });

    document.querySelector(".content").classList.add("fade-out");

    setTimeout(() => {
        document.getElementById("page4").classList.add("hidden");
        document.getElementById("thankyou").classList.remove("hidden");
        document.querySelector(".content").classList.remove("fade-out");
    }, 600);
}
</script>

</body>
</html>
