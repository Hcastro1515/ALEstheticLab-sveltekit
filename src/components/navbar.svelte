<script lang="ts">
	import { Navbar, NavBrand, NavLi, NavUl, NavHamburger } from 'flowbite-svelte';
</script>


<Navbar let:hidden let:toggle>
    <NavBrand href="/">
        <span class="self-center whitespace-nowrap text-xl font-semibold dark:text-white">
            AlaestheticLab
        </span>
    </NavBrand>
    <NavHamburger on:click={toggle} />
    <NavUl {hidden}>
        <NavLi href="/" active={true}>Home</NavLi>
        <NavLi href="/about">Citas</NavLi>
        <NavLi href="/services">Servicios</NavLi>
        <NavLi href="/pricing">Reports</NavLi>
        <NavLi href="/contact">Empleados</NavLi>
    </NavUl>
</Navbar>
