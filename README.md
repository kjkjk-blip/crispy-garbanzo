<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>BLACK//NODE TERMINAL</title>

<style>
    * {
        box-sizing: border-box;
    }

    body {
        margin: 0;
        background: #000;
        color: #00ff66;
        font-family: "Courier New", monospace;
        overflow: hidden;
    }

    .terminal {
        width: 100vw;
        height: 100vh;
        padding: 20px;
        overflow: auto;
        text-shadow: 0 0 8px #00ff66;
    }

    .top {
        border-bottom: 1px solid #00ff66;
        padding-bottom: 10px;
        margin-bottom: 15px;
    }

    .logo {
        font-size: 25px;
        font-weight: bold;
    }

    .sub {
        color: #00aa44;
        font-size: 12px;
    }

    #output {
        white-space: pre-wrap;
        line-height: 1.5;
    }

    .input-line {
        display: flex;
        margin-top: 10px;
    }

    .prompt {
        margin-right: 8px;
    }

    #command {
        background: transparent;
        border: none;
        outline: none;
        color: #00ff66;
        font-family: inherit;
        font-size: 16px;
        width: 100%;
        text-shadow: 0 0 8px #00ff66;
    }

    .red {
        color: #ff3333;
        text-shadow: 0 0 8px #ff3333;
    }

    .yellow {
        color: #ffff33;
    }

    .cyan {
        color: #00ffff;
    }

    .hidden {
        display: none;
    }
</style>
</head>

<body>

<div class="terminal">

    <div class="top">
        <div class="logo">[ BLACK//NODE ]</div>
        <div class="sub">
            SECURE TERMINAL // SIMULATION MODE // NO REAL CONNECTION
        </div>
    </div>

    <div id="output"></div>

    <div class="input-line">
        <span class="prompt">root@blacknode:~$</span>
        <input id="command" autocomplete="off" autofocus>
    </div>

</div>

<script>

const output = document.getElementById("output");
const command = document.getElementById("command");

let users = [
    {
        username: "ShadowX",
        password: "V0id_7392!"
    },
    {
        username: "NeoGhost",
        password: "Matrix_4821"
    },
    {
        username: "K1LLERBYTE",
        password: "Cyber_9907"
    },
    {
        username: "DarkNode",
        password: "N0de_5518"
    }
];

function print(text, delay = 0) {

    setTimeout(() => {
        output.innerHTML += text + "\n";
        window.scrollTo(0, document.body.scrollHeight);
    }, delay);
}

function randomHex(length) {

    const chars = "0123456789ABCDEF";
    let result = "";

    for (let i = 0; i < length; i++) {
        result += chars[Math.floor(Math.random() * chars.length)];
    }

    return result;
}

function randomIP() {

    return (
        Math.floor(Math.random() * 223 + 1) + "." +
        Math.floor(Math.random() * 255) + "." +
        Math.floor(Math.random() * 255) + "." +
        Math.floor(Math.random() * 255)
    );
}

function boot() {

    print("<span class='cyan'>Initializing BLACK//NODE...</span>");
    print("[ OK ] Kernel loaded");
    print("[ OK ] Encryption module loaded");
    print("[ OK ] Terminal interface loaded");
    print("[ OK ] Simulation engine loaded");
    print("");

    setTimeout(() => {
        print("<span class='yellow'>WARNING:</span> This terminal is a visual simulation.");
        print("No real systems are contacted.");
        print("");
        print("Type <span class='cyan'>help</span> to display available commands.");
        print("");
    }, 800);
}

function help() {

    print("");
    print("<span class='cyan'>AVAILABLE COMMANDS</span>");
    print("--------------------------------");
    print("help       → afficher les commandes");
    print("clear      → nettoyer le terminal");
    print("users      → afficher les comptes fictifs");
    print("scan       → lancer un faux scan");
    print("network    → afficher un faux réseau");
    print("decrypt    → lancer une fausse simulation");
    print("status     → afficher l'état du système");
    print("matrix     → mode caractères");
    print("login      → simulation de connexion");
    print("");
}

function showUsers() {

    print("");
    print("<span class='cyan'>LOCAL USER DATABASE</span>");
    print("--------------------------------");

    users.forEach((user, index) => {

        print(
            "[" + (index + 1) + "] " +
            "USER: " + user.username +
            " | PASSWORD: " + user.password
        );

    });

    print("--------------------------------");
    print("DATABASE TYPE: FICTIONAL");
    print("");
}

function scan() {

    print("");
    print("<span class='cyan'>Starting simulated network scan...</span>");

    let progress = 0;

    const interval = setInterval(() => {

        progress += 10;

        let bar = "";

        for (let i = 0; i < progress / 5; i++) {
            bar += "█";
        }

        for (let i = progress / 5; i < 20; i++) {
            bar += "░";
        }

        output.innerHTML +=
            "SCAN [" + bar + "] " + progress + "%\n";

        if (progress >= 100) {

            clearInterval(interval);

            print("");
            print("<span class='cyan'>SCAN COMPLETE</span>");
            print("--------------------------------");
            print("Node: " + randomIP());
            print("Node: " + randomIP());
            print("Node: " + randomIP());
            print("Node: " + randomIP());
            print("");
            print("<span class='yellow'>No real network was scanned.</span>");
            print("");
        }

    }, 180);
}

function network() {

    print("");
    print("<span class='cyan'>VIRTUAL NETWORK MAP</span>");
    print("--------------------------------");

    print("CORE-01  ---- NODE-" + randomHex(4));
    print("    |");
    print("    +---- NODE-" + randomHex(4));
    print("    |");
    print("    +---- NODE-" + randomHex(4));
    print("              |");
    print("              +---- GATE-" + randomHex(3));

    print("");
}

function decrypt() {

    print("");
    print("<span class='cyan'>SIMULATED DECRYPTION</span>");
    print("--------------------------------");

    let i = 0;

    const interval = setInterval(() => {

        print(
            "KEY[" +
            String(i).padStart(2, "0") +
            "] :: " +
            randomHex(16)
        );

        i++;

        if (i >= 12) {

            clearInterval(interval);

            print("");
            print("<span class='yellow'>Simulation finished.</span>");
            print("No real password or file was decrypted.");
            print("");
        }

    }, 120);
}

function status() {

    print("");
    print("<span class='cyan'>SYSTEM STATUS</span>");
    print("--------------------------------");
    print("CPU LOAD      : " + Math.floor(Math.random() * 60 + 20) + "%");
    print("MEMORY        : " + Math.floor(Math.random() * 5000 + 2000) + " MB");
    print("ENCRYPTION    : AES-SIM");
    print("FIREWALL      : ACTIVE");
    print("CONNECTION    : LOCAL SIMULATION");
    print("THREAT LEVEL  : 0");
    print("--------------------------------");
    print("");
}

function matrix() {

    let symbols = "01ABCDEF#$%&@";

    for (let i = 0; i < 30; i++) {

        let line = "";

        for (let j = 0; j < 70; j++) {
            line += symbols[Math.floor(Math.random() * symbols.length)];
        }

        print(line);
    }

    print("");
}

function login() {

    print("");
    print("<span class='cyan'>LOGIN SIMULATION</span>");
    print("--------------------------------");
    print("Username: ShadowX");
    print("Password: ********");
    print("");
    print("<span class='yellow'>ACCESS GRANTED — SIMULATION ONLY</span>");
    print("");
}

command.addEventListener("keydown", function(event) {

    if (event.key !== "Enter") return;

    const cmd = command.value.trim().toLowerCase();

    if (!cmd) return;

    print(
        "<span class='cyan'>root@blacknode:~$</span> " +
        command.value
    );

    command.value = "";

    switch (cmd) {

        case "help":
            help();
            break;

        case "clear":
            output.innerHTML = "";
            break;

        case "users":
            showUsers();
            break;

        case "scan":
            scan();
            break;

        case "network":
            network();
            break;

        case "decrypt":
            decrypt();
            break;

        case "status":
            status();
            break;

        case "matrix":
            matrix();
            break;

        case "login":
            login();
            break;

        default:
            print(
                "<span class='red'>Command not found:</span> " +
                cmd
            );
            print("Type 'help' for available commands.");
            print("");
    }

});

boot();

</script>

</body>
</html># crispy-garbanzo
un jeu quizz
