<template>
  <nav class="navbar navbar-expand-lg style-2" id="navbar">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">
        <img
          class="black-logo"
          src="../assets/img/egsppc-logo.png"
          alt="black-logo"
        />
      </a>
      <button
        class="navbar-toggler text-decoration-none"
        type="button"
        data-bs-toggle="offcanvas"
        data-bs-target="#navbarOffcanvas"
        aria-controls="navbarOffcanvas"
      >
        <span class="burger-menu">
          <span class="top-bar"></span>
          <span class="middle-bar"></span>
          <span class="bottom-bar"></span>
        </span>
      </button>
      <div class="collapse navbar-collapse">
        <ul class="navbar-nav m-auto">
          <li v-for="(item, index) in navItems" :key="index" class="nav-item">
            <a
              :href="item.link || 'javascript:void(0)'"
              class="dropdown-toggle nav-link"
              :class="{ active: item.active }"
              @click="toggleDropdown(index)"
            >
              {{ item.label }}
            </a>
            <ul
              v-if="item.subItems && item.subItems.length"
              class="dropdown-menu"
              :class="{ show: item.showDropdown }"
            >
              <li
                v-for="(subItem, subIndex) in item.subItems"
                :key="subIndex"
                class="nav-item"
              >
                <a
                  :href="subItem.link"
                  class="nav-link"
                  @click="toggleSubDropdown(index, subIndex)"
                >
                  {{ subItem.label }}
                </a>
                <ul
                  v-if="subItem.subItems && subItem.subItems.length"
                  class="dropdown-menu"
                  :class="{ show: subItem.showDropdown }"
                >
                  <li
                    v-for="(dept, deptIndex) in subItem.subItems"
                    :key="deptIndex"
                    class="nav-item"
                  >
                    <a :href="dept.link" class="nav-link">{{ dept.label }}</a>
                  </li>
                </ul>
              </li>
            </ul>
          </li>
        </ul>
      </div>
    </div>
  </nav>

  <div
    class="responsive-navbar offcanvas offcanvas-end border-0"
    data-bs-backdrop="static"
    tabindex="-1"
    id="navbarOffcanvas"
    aria-modal="true"
    role="dialog"
  >
    <div class="offcanvas-header">
      <a href="#" class="logo d-inline-block">
        <img
          src="../assets/img/egsppc-white-logo.png"
          style="width: 70%"
          alt="logo"
        />
      </a>
      <button
        type="button"
        class="close-btn bg-transparent position-relative lh-1 p-0 border-0"
        data-bs-dismiss="offcanvas"
        aria-label="Close"
      >
        <i class="ri-close-fill"></i>
      </button>
    </div>
    <div class="offcanvas-body">
      <ul class="responsive-menu">
        <li
          v-for="(item, index) in navItems"
          :key="index"
          class="responsive-menu-list"
        >
          <a
            :href="item.link || 'javascript:void(0)'"
            @click="toggleDropdown(index)"
            class="nav-link"
          >
            {{ item.label }}
          </a>
          <ul
            v-if="item.subItems && item.subItems.length"
            class="responsive-menu-items"
            :class="{ show: item.showDropdown }"
          >
            <li
              v-for="(subItem, subIndex) in item.subItems"
              :key="subIndex"
              class="nav-item"
            >
              <a
                :href="subItem.link"
                @click="toggleSubDropdown(index, subIndex)"
                class="nav-link"
              >
                {{ subItem.label }}
              </a>
              <ul
                v-if="subItem.subItems && subItem.subItems.length"
                class="responsive-menu-items"
                :class="{ show: subItem.showDropdown }"
              >
                <li
                  v-for="(dept, deptIndex) in subItem.subItems"
                  :key="deptIndex"
                  class="nav-item"
                >
                  <a :href="dept.link" class="nav-link">{{ dept.label }}</a>
                </li>
              </ul>
            </li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  name: "Header",
  data() {
    return {
      navItems: [
        {
          label: "Home",
          link: "",
          active: true,
        },
        { label: "About Us", link: "about.html" },
        { label: "Programs", link: "programs.html" },
        { label: "Facilities", link: "facilities.html" },
        {
          label: "Academics",
          link: "javascript:void(0)",
          showDropdown: false,
          subItems: [
            {
              label: "University Overview",
              link: "university-overview.html",
            },
            {
              label: "Blog",
              link: "javascript:void(0)",
              showDropdown: false,
              subItems: [
                { label: "Blog Style One", link: "blog-style-one.html" },
                { label: "Blog Style Two", link: "blog-style-two.html" },
                { label: "Blog Details", link: "blog-details.html" },
              ],
            },
            { label: "Register Now", link: "register.html" },
            { label: "Log In Now", link: "login.html" },
            { label: "Application Form", link: "application.html" },
            { label: "Faculty", link: "faculty.html" },
            { label: "Support & Guidance", link: "guidance-support.html" },
            { label: "Privacy Policy", link: "privacy-policy.html" },
            { label: "Terms & Conditions", link: "terms-conditions.html" },
          ],
        },
        { label: "Placements", link: "placements.html" },
        { label: "Alumni", link: "alumni.html" },
      ],
    };
  },
  methods: {
    toggleDropdown(index) {
      this.navItems[index].showDropdown = !this.navItems[index].showDropdown;
    },
    toggleSubDropdown(index, subIndex) {
      this.navItems[index].subItems[subIndex].showDropdown =
        !this.navItems[index].subItems[subIndex].showDropdown;
    },
  },
};
</script>

<style scoped>
.black-logo {
  width: 100%;
  max-width: 270px;
  height: auto;
}

@media (max-width: 576px) {
  .black-logo {
    max-width: 150px;
  }
}

.offcanvas-body .logo img {
  width: 100%;
  max-width: 80%;
  height: auto;
}

.dropdown-menu {
  display: none;
}

.dropdown-menu.show {
  display: block;
}

.nav-item:hover .dropdown-menu {
  display: block;
}

.dropdown-menu .dropdown-menu {
  margin-left: 15px;
}

.responsive-menu-items {
  display: none;
}

.responsive-menu-items.show {
  display: block;
}
</style>
