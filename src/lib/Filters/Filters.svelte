<script lang="ts">
    import { writable } from "svelte/store";
    import Filter from "./Filter.svelte";

    let filters = [
        {
            displayName: null,
            name: "general",
            multiselect: true,
            options: [
                "Here to talk",
                "Certified advisor"
            ]
        },
        {
            name: "grade",
            displayName: "Grade",
            multiselect: false,
            options: [
                "9th",
                "10th",
                "11th",
                "12th",
                "Other"
            ]
        },
        {
            name: "school",
            displayName: "School",
            multiselect: false,
            options: [
                "Moorpark HS",
                "The HS at Moorpark College",
                "Newbury Park HS",
                "Simi Valley HS",
                "Westlake HS",
                "Thousand Oaks HS"
            ]
        },
        {
            name: "gender",
            displayName: "Gender",
            multiselect: false,
            options: [
                "Male",
                "Female",
                "Non-Binary",
                "Other"
            ]
        },
        {
            name: "interests",
            displayName: "Interests and Expertise",
            multiselect: true,
            options: [
                "๐ Sports",
                "๐ต Music",
                "๐ญ Drama",
                "๐ป Tech",
                "๐จ Art",
                "๐ผ Career",
                "๐ College Prep"
            ]
        },
        {
            name: "academics",
            displayName: "Academics",
            multiselect: true,
            options: [
                "โ Math",
                "๐งช Science",
                "๐ English",
                "๐ Foreign Language",
                "๐ History",
                "โ Other Subject"
            ]
        },
    ]

    export let filterStore = writable([]);
    export let isAdvisor = false;
</script>

<div>
    <h3>Select all that apply</h3>
    {#each filters as filter}
        {#if filter.displayName}
        <h4>{filter.displayName} {isAdvisor && !filter.multiselect ? "(select one)" : ""}</h4>
        {/if}
        <div class="filterList">
        {#each filter.options as option}
            <Filter multiselect={isAdvisor ? filter.multiselect : true} category={filter.name} name={option} filterStore={filterStore} />
        {/each}
        </div>
    {/each}
</div>
<style>
    .filterList {
        flex-grow: 1;
        display: flex;
        flex-wrap: wrap;
        gap: 10px;
    }
</style>