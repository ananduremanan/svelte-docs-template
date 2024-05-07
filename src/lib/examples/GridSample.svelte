<script lang="ts">
  import Grid from "@grampro/svelte-block/Grid.svelte";
  import { onMount } from "svelte";
  import ImageAction from "./ImageAction.svelte";

  const gitDataColumns: any[] = [
    { field: "id", width: "200", textAlign: "Right", filter: true },
    {
      field: "imgUrl",
      width: "200",
      textAlign: "Right",
      template: ImageAction,
      showTemplateInExport: true,
    },
    { field: "userName", width: "100", filter: true },
    { field: "repo", width: "100", textAlign: "Right" },
    { field: "repoUrl", headerText: "Repo URL", width: "200" },
  ];

  const getData = async () => {
    let dataArray = [];
    try {
      const res = await fetch(
        "https://raw.githubusercontent.com/json-iterator/test-data/master/large-file.json"
      );
      const data = await res.json();
      if (data) {
        dataArray = data.map((item: any) => {
          return {
            id: item.id,
            userName: item.actor.login,
            repo: item.repo.name,
            repoUrl: item.repo.url,
            imgUrl: item.actor.avatar_url,
          };
        });
      }

      return dataArray;
    } catch (error) {
      console.error(error);
    }
  };

  let gitData: any[] = [];

  onMount(async () => {
    gitData = await getData();
  });
</script>

<Grid
  columns={gitDataColumns}
  dataSource={gitData}
  pageSettings={{ pageNumber: 10 }}
  enableSearch
/>
