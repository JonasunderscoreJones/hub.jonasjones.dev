<script>
    import { onMount } from "svelte";
    // Array of site data
    let sites = [];

    onMount(async () => {
        const res = await fetch(
            "https://cdn.jonasjones.dev/api/hub/blobs.json"
        );
        sites = await res.json();
    });
  </script>

  <style>

    .container {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      padding: 20px;
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
    }

    .site-card {
      background-color: darkgray;
      border-radius: 8px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      margin: 15px;
      width: 300px;
      overflow: hidden;
      text-align: center;
    }

    .site-card img {
      width: 100%;
      height: 150px;
      object-fit: cover;
    }

    .site-card .content {
      padding: 20px;
    }

    .site-card h3 {
      margin: 10px 0;
      font-size: 1.2rem;
      color: #333;
    }

    .site-card p {
      font-size: 0.9rem;
      color: #666;
    }

    .site-card a {
      display: inline-block;
      margin-top: 10px;
      padding: 8px 15px;
      background-color: #0073e6;
      color: white;
      text-decoration: none;
      border-radius: 4px;
      transition: background-color 0.3s;
    }

    .site-card a:hover {
      background-color: #005bb5;
    }
  </style>

  <div class="container">
    {#each sites as { name, description, image, link }}
      <div class="site-card">
        <img src={image} alt={name} />
        <div class="content">
          <h3>{name}</h3>
          <p>{description}</p>
          <a href={link} target="_blank" rel="noopener noreferrer">Visit Site</a>
        </div>
      </div>
    {/each}
  </div>
