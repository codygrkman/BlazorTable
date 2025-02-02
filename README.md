# BlazorTable
[![Demo (from original BlazorTable)](https://img.shields.io/badge/Live-Demo-Blue?style=flat-square)](https://BlazorTable.netlify.com/)
[![Nuget (with prereleases)](https://img.shields.io/nuget/vpre/BlazorTableExtended.svg?style=flat-square)](https://www.nuget.org/packages/BlazorTableExtended)
[![Nuget (with prereleases)](https://img.shields.io/nuget/dt/BlazorTableExtended.svg?style=flat-square)](https://www.nuget.org/packages/BlazorTableExtended)

Blazor Table Component with Sorting, Paging and Filtering.
- This is a fork of Ivan Josipovic's [BlazorTable](https://github.com/IvanJosipovic/BlazorTable) with the addition of native Blazor `@ondblclick` support.

[![Sample Gif](https://raw.githubusercontent.com/IvanJosipovic/BlazorTable/master/BlazorTable.gif)](/BlazorTable.gif)

## Install

- Add [BlazorTable Nuget](https://www.nuget.org/packages/BlazorTableExtended)
  - dotnet add package BlazorTable
- Add to the index.html or _Hosts.cshtml
  - `<script src="_content/BlazorTable/BlazorTable.min.js"></script>`
- Add call to Program.cs or Startup.cs
  - Services.AddBlazorTable();

Note: If installing `BlazorTable` in a hosted Blazor WASM application, these steps should be performed in the [WASM Client](https://docs.microsoft.com/en-us/aspnet/core/blazor/hosting-models?view=aspnetcore-5.0#blazor-webassembly-1) project.

## Features
- Column Reordering
- Edit Mode ([Template Switching](https://github.com/IvanJosipovic/BlazorTable/blob/master/src/BlazorTable.Sample.Shared/Pages/EditMode.razor))
- Client Side
	- Paging
	- Sorting
    - Filtering
      	- Strings
        - Numbers
        - Dates
        - Enums
        - Custom Component
## Dependencies
- Bootstrap 4 CSS

## Sample
[Example Page](https://github.com/IvanJosipovic/BlazorTable/blob/master/src/BlazorTable.Sample.Shared/Pages/Index.razor)

```csharp
<Table TableItem="PersonData" Items="data" PageSize="15">
    <Column TableItem="PersonData" Title="Id" Field="@(x => x.id)" Sortable="true" Filterable="true" Width="10%" />
    <Column TableItem="PersonData" Title="First Name" Field="@(x => x.first_name)" Sortable="true" Filterable="true" Width="20%" />
    <Column TableItem="PersonData" Title="Last Name" Field="@(x => x.last_name)" Sortable="true" Filterable="true" Width="20%" />
    <Column TableItem="PersonData" Title="Email" Field="@(x => x.email)" Sortable="true" Filterable="true" Width="20%">
        <Template>
            <a href="mailto:@context.email">@context.email</a>
        </Template>
    </Column>
    <Column TableItem="PersonData" Title="Confirmed" Field="@(x => x.confirmed)" Sortable="true" Filterable="true" Width="10%" />
    <Column TableItem="PersonData" Title="Price" Field="@(x => x.price)" Sortable="true" Filterable="true" Width="10%" Format="C" Align="Align.Right" />
    <Column TableItem="PersonData" Title="Created Date" Field="@(x => x.created_date)" Sortable="true" Width="10%">
        <Template>
            @context.created_date.ToShortDateString()
        </Template>
    </Column>
    <Pager ShowPageNumber="true" ShowTotalCount="true" />
</Table>
```
