<script>
  import MapView from "@arcgis/core/views/MapView";
  import "@arcgis/core/assets/esri/themes/light/main.css";

  let centerText;
  const createMap = (domNode) => {
    const view = new MapView({
      container: domNode,
      map: {
        basemap: "oceans",
        ground: "world-topobathymetry",
        
      },
      zoom: 5,
      center: [-5.97317, 37.38283],
    });
    view.watch("center", (center) => {
      const {latitude, longitude} = center;
      centerText = `Posicion: Latitud: ${latitude.toFixed(4)} | Longitud: ${longitude.toFixed(4)}`;
  })

};
</script>

<main>
  <div class="view" use:createMap></div>
  {#if centerText}
  <p>{centerText}</p>
  {/if}
</main>

<style>
    .view {
    height: 800px;
    width: 1200px;
  }
</style>
