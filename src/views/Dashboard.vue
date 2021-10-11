<template>
  Dashboard
</template>

<script>
export default {
  data() {
    return {};
  },
  created() {
    // 取cookie裡的token
    const token = document.cookie.replace(/(?:(?:^|.*;\s*)token\s*=\s*([^;]*).*$)|^.*$/, '$1');
    // token放到header
    this.axios.defaults.headers.common.Authorization = token;
    const checkApiPath = `${process.env.VUE_APP_API}api/user/check`;
    this.$http.post(checkApiPath).then((res) => {
      console.log(res);
      if (!res.data.success) {
        this.$router.push('/login');
      }
    });
  },
};
</script>
