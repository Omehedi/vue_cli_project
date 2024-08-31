
<template>
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <div class="container-fluid">

            <a class="navbar-brand" href="#">Super Store</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <form @submit.prevent="search" class="d-flex ms-auto" role="search">
                    <input v-model="keyword" class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
                    <button class="btn btn-outline-success me-2" type="submit">Search</button>
                </form>
                <!-- Dropdown for Login/Logout -->
                <div class="dropdown">
                    <button class="btn btn-secondary dropdown-toggle" type="button" id="userDropdown" data-bs-toggle="dropdown" aria-expanded="false">
                        <i class="fas fa-user"></i> Account
                    </button>
                    <ul class="dropdown-menu dropdown-menu-end" aria-labelledby="userDropdown">
                        <li>
                            <a class="dropdown-item" href="#">
                                <i class="fas fa-sign-in-alt"></i> Login
                            </a>
                        </li>
                        <li>
                            <a class="dropdown-item" href="#">
                                <i class="fas fa-sign-out-alt"></i> Logout
                            </a>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </nav>
</template>

<script>
    export default {
        name: 'Navbar',
        data() {
            return {
                keyword: ''
            }
        },
        methods: {
            search() {
                this.$emit('search', this.keyword);
            }
        }
    };
</script>

<style scoped>

</style>











<!--<template>-->
<!--    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">-->
<!--        <div class="container-fluid">-->
<!--            &lt;!&ndash; Logo &ndash;&gt;-->
<!--            <img src="data:image/png;base64,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"-->
<!--             alt="Super Store Logo"-->
<!--                 class="navbar-brand-logo"-->
<!--                 style="height: 50px; width: auto;">-->

<!--            &lt;!&ndash; Navbar Title &ndash;&gt;-->
<!--            <a class="navbar-brand" href="#" style="font-weight: bold; font-size: 1.5rem; color: #fff;">Super Store</a>-->

<!--            &lt;!&ndash; Toggle Button for Mobile View &ndash;&gt;-->
<!--            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">-->
<!--                <span class="navbar-toggler-icon"></span>-->
<!--            </button>-->

<!--            &lt;!&ndash; Navbar Links &ndash;&gt;-->
<!--            <div class="collapse navbar-collapse" id="navbarNav">-->
<!--                <ul class="navbar-nav ml-auto">-->
<!--                    <li class="nav-item">-->
<!--                        <a class="nav-link active" aria-current="page" href="#">Home</a>-->
<!--                    </li>-->
<!--                    <li class="nav-item">-->
<!--                        <a class="nav-link" href="#">Features</a>-->
<!--                    </li>-->
<!--                    <li class="nav-item">-->
<!--                        <a class="nav-link" href="#">Pricing</a>-->
<!--                    </li>-->
<!--                    <li class="nav-item">-->
<!--                        <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">Disabled</a>-->
<!--                    </li>-->
<!--                </ul>-->
<!--            </div>-->
<!--        </div>-->
<!--    </nav>-->
<!--</template>-->

<!--<style scoped>-->
<!--    .navbar-brand-logo {-->
<!--        max-height: 50px; /* Adjust as needed */-->
<!--        margin-right: 15px;-->
<!--    }-->
<!--    .navbar-brand {-->
<!--        font-weight: bold;-->
<!--        font-size: 1.5rem; /* Adjust size as needed */-->
<!--        color: #fff; /* Color of the text */-->
<!--    }-->
<!--</style>-->







