<script>
  import Header from './components/header/Header.svelte';
  import Footer from './components/footer/Footer.svelte';

  //tabs
  let items = ['Current Polls', 'Add New Poll'];
  let activeItem = 'Current Polls';
</script>

<Header />
<main>
  <p>
    Lorem ipsum dolor sit amet consectetur, adipisicing elit. Tempora, saepe.
    Tempora, veniam tenetur non vel ex dignissimos recusandae consequatur,
    eligendi amet sunt similique voluptatum deserunt consectetur rem? Tenetur,
    nemo quae.
  </p>
</main>
<Footer />

<style>
  main {
    max-width: 960px;
    margin: 40px auto;
  }
</style>
