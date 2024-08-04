<template>
  <div class="top-header-area style-2">
    <div class="container-fluid">
      <div class="row align-items-center">
        <div class="col-lg-6 col-md-6">
          <div class="top-header-list style-2">
            <ul class="list-unstyled ps-0 mb-0">
              <li class="d-inline-block">
                <a
                  class="text-decoration-none d-flex align-items-center"
                  href="tel:+919942502245"
                >
                  <i class="flaticon-call"></i>
                  +91 9942 502 245
                </a>
              </li>
              <li class="d-inline-block">
                <a
                  class="text-decoration-none d-flex align-items-center"
                  href=""
                >
                  <i class="ri-message-line"></i>
                  <span class="__cf_email__">contact@egsppc.ac.in</span>
                </a>
              </li>
            </ul>
          </div>
        </div>
        <div class="col-lg-6 col-md-6">
          <div class="top-header-social-list text-end">
            <ul class="list-unstyled ps-0 mb-0">
              <li class="d-inline-block">
                <ul class="list-unstyled ps-0 mb-0 pages-link">
                  <li
                    v-for="link in links"
                    :key="link.name"
                    class="d-inline-block"
                  >
                    <a class="text-decoration-none" :href="link.url">{{
                      link.name
                    }}</a>
                  </li>
                </ul>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      links: [
        { name: "Mandatory Disclosures", url: "" },
        { name: "Admission Forms", url: "" },
        { name: "Downloads", url: "" },
        { name: "Contact us", url: "" },
      ],
    };
  },
};
</script>

<style scoped>
/* Add your styles here */
</style>
