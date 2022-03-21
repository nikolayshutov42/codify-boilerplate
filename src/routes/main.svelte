<script>
  let language = 'ru'
</script>



<div class="main">
  <a href="/">Main page</a>
  <a href={`/${language}/about`}>About us</a>
  <a href={`/${language}/contacts`}>Contacts</a>


</div>

<style>
.main {
  display: flex;
  justify-content: center;
  flex-direction: column;
  margin: 50px;
}
</style>
