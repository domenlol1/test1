<template>
    <div class="navigation">
        <div class="elements">
            <div class="levo">
                <a href="" class="a1">Sončna očala</a>
                <a href="index" class="a1">Trgovina</a>
            </div>
            <form action="." method="post">
                <input class="bar" type="text" name="search" id="search" placeholder="Search...">
            </form>
            <div class="desno">
                <div class="desno" v-if="loggedin == false">
                    <button class="roundbutton1"><a href="login" class="roundbutton11">login</a></button>
                    <button class="roundbutton2"><a href="signup" class="roundbutton22">signup</a></button>
                </div>
                <div class="desno" v-else>
                    <button class="roundbutton2 roundbutton22" v-on:click="removecookie">logout</button>
                </div>
                <a href="cart"><img src="../assets/carticon.jpg" style="width: 30px; height: 30px;"></a>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            loggedin: false,
        }
    },
    methods: {
        removecookie() {
            document.cookie = "ime=; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/;";
            document.cookie = "UID=; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/;";
            this.loggedin = false;
            window.location.href = "";
        },
        getCookie(cname) {
            let name = cname + "=";
            let ca = document.cookie.split(';');
            for (let i = 0; i < ca.length; i++) {
                let c = ca[i];
                while (c.charAt(0) == ' ') {
                    c = c.substring(1);
                }
                if (c.indexOf(name) == 0) {
                    return c.substring(name.length, c.length);
                }
            }
            return "";
        },
        setCookie(cname, cvalue, exdays) {
            const d = new Date();
            d.setTime(d.getTime() + exdays * 24 * 60 * 60 * 1000);
            let expires = "expires=" + d.toUTCString();
            document.cookie = cname + "=" + cvalue + ";" + expires + ";path=/";
        },
        checkLogin() {
            if (this.getCookie("ime") != "") {
                this.loggedin = true;
            }
        },
    },
    mounted() {
        this.checkLogin();
    },
}
</script>

<style scoped>
.navigation {
    background-color: white;
    box-shadow: 0 4px 2px rgb(111 111 135 / 5%), 0 4px 10px rgb(111 111 135 / 25%);
    padding: 20px;
    width: 100%;
    position: fixed;
    left: 0;
    top: 0;
    z-index: 100000;
    pointer-events: auto;
}

.elements {
    align-items: center;
    width: 1024px;
    margin: auto;
    display: flex;
    justify-content: space-between;
}

.levo {
    display: flex;
    gap: 30px;
}

.desno {
    display: flex;
    gap: 15px;
}

.roundbutton1 {
    padding: 10px 20px;
    border: none;
    border-radius: 20px;
    background-color: #000000;
    color: #1aaaaf;
    text-align: center;
    text-decoration: none;
    cursor: pointer;
    font-weight: bolder;
    font-family: sans-serif;
}

.roundbutton11 {
    border: none;
    border-radius: 20px;
    background-color: #000000;
    color: #1aaaaf;
    text-align: center;
    text-decoration: none;
    cursor: pointer;
    font-weight: bolder;
    font-family: sans-serif;
}

.roundbutton2 {
    padding: 10px 20px;
    border: none;
    border-radius: 20px;
    background-color: #1aaaaf;
    color: rgb(0, 0, 0);
    text-align: center;
    text-decoration: none;
    cursor: pointer;
    font-weight: bolder;
    font-family: sans-serif;
}

.roundbutton22 {
    border: none;
    border-radius: 20px;
    background-color: #1aaaaf;
    color: rgb(0, 0, 0);
    text-align: center;
    text-decoration: none;
    cursor: pointer;
    font-weight: bolder;
    font-family: sans-serif;
}

.a1 {
    text-decoration: none;
    --link-color: #000000;
    color: var(--link-color);
    font-size: 16px;
}

.bar {
    display: flex;
    height: 40px;
    width: 500px;
    margin-left: 20px;
    background-color: rgb(191, 191, 191);
    border-radius: 20px;
    outline: 0;
    border: 0;
    padding: 3px 16px;
}
</style>
