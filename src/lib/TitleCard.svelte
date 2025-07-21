<script>
  let { title, subtitle } = $props();
</script>

<div class="title-card">
  <div class="content">
    <h1>{title}</h1>
    <p>{subtitle}</p>
  </div>
</div>

<style>
  .title-card {
    background-image: url(https://images.unsplash.com/photo-1603108158810-dbec8a00dae7?q=80&w=1740&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D);
    background-position: center;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    box-sizing: border-box;
    font-family: Georgia, "Times New Roman", Times, serif;
  }

  .content {
    max-width: 1100px;
    padding: 5px;
    color: white;
  }

  h1 {
    font-size: 37px;
    margin: 0;
    color: black;
    text-shadow: 1px 1px 0 gray;
    background-color: #feffe8;
    font-style: italic;
  }

  p {
    font-size: 1.3rem;
    color: black;
    text-shadow: 1px 1px 0 gray;
    margin-top: 1rem;
  }

  @media (max-width: 600px) {
    h1 {
      font-size: 2.2rem;
    }

    p {
      font-size: 400rem;
    }
  }
</style>
