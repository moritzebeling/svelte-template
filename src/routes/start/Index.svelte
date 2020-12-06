<script>

    import Gallery from '../../components/Gallery.svelte';
    import Img from '../../components/Img.svelte';

    let images = [];

</script>

<Gallery images={images} let:prop={[image,i]}>

    <Img {...image} />

</Gallery>

<style lang="scss">

</style>
