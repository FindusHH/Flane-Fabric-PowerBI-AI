# Work with PBIP Files in Visual Studio Code

## PBIX, PBIP, and PBIR

A `.pbix` is a single Power BI Desktop file. Depending on the connection mode, it can package a report, a semantic model, and imported data. A Power BI Project (PBIP) separates the report and semantic model into `*.Report` and `*.SemanticModel` folders. The `.pbip` file is a shortcut to the report; you can also open the report through `definition.pbir`. A relative model reference (`byPath`) opens the local semantic model alongside the report.

PBIR is the enhanced, schema-documented format for the **report** definition. The `*.Report` folder alone is not a full replacement for a PBIX with an embedded model. Even a complete PBIP project checked out from Git can open without imported data: the local `.pbi\cache.abf` is ignored by default. PBIP is useful for Git diffs and collaborative editing; choose PBIX when you need a single file to hand off. Power BI Desktop can publish a PBIP project using a temporary PBIX, including any local model data cache. Git and API deployment paths deploy metadata rather than that local cache.

## What you can edit

| File or folder | Typical changes |
| --- | --- |
| `*.Report\definition\pages\<page-id>\page.json` | Change the visible page name (`displayName`), page size, formatting, or page-level filters. |
| `*.Report\definition\pages\pages.json` | Change page order or the active page. |
| `*.Report\definition\pages\<page-id>\visuals\<visual-id>\visual.json` | Change a visual's position, size, formatting, filters, or field bindings. Referenced columns and measures must exist in the model. |
| `*.Report\definition\report.json` | Change report-wide filters or formatting. This is the schema-documented PBIR file, not the legacy file with the same name. |
| `*.Report\definition\bookmarks\` | Edit bookmark definitions or order. When copying bookmarks between reports, verify that the referenced pages and visuals are present. |
| `*.SemanticModel\definition\*.tmdl` and its subfolders | Edit DAX measures, format strings, table and column properties, relationships, and Power Query M expressions. Test the affected visuals and refresh the model when you change queries. |

Use the `$schema` reference in PBIR JSON files for validation and completion in VS Code. For the model, install Microsoft's [TMDL extension for VS Code](https://marketplace.visualstudio.com/items?itemName=analysis-services.TMDL). Schema validation doesn't guarantee that references are valid or that a report behaves as intended after the change.

## What to leave to Power BI Desktop

| File or object | Limitation |
| --- | --- |
| `*.Report\report.json` at the root of the report folder | This is **PBIR-Legacy**. External editing isn't supported. Don't confuse it with `*.Report\definition\report.json`. |
| `mobileState.json`, `semanticModelDiagramLayout.json`, and `*.SemanticModel\diagramLayout.json` | External editing isn't supported. |
| `*.Report\definition.pbir` | Contains the model reference. It's excluded from the preview workflow for applying external changes in an open Desktop session. Leave it unchanged for routine report edits. |
| `.pbi\cache.abf` | Binary local data cache, not a text definition. The external reload feature doesn't reload it. |
| `.pbi\unappliedChanges.json` | Apply pending Power Query changes in Desktop before editing model expressions in VS Code. Otherwise, applying the pending changes later can overwrite your edits. |
| Automatically generated date tables | Don't edit them externally. Use Power BI Desktop to manage automatic date/time behavior. |

## Recommended workflow

1. Save your changes in Power BI Desktop and take a backup or create a Git checkpoint. Open the project root in VS Code so both the report and model folders are visible.
2. Make one small change and save as **UTF-8 without BOM**. As a first test, find the `page.json` whose `displayName` is `Sales Overview` and change only that value. Leave the internal page ID and folder name unchanged. To test a model edit, change the `formatString` of `Total Sales` in `*.SemanticModel\definition\tables\Sales.tmdl` without changing the DAX formula.
3. In Power BI Desktop, select **Apply external changes** when the banner appears, or close and reopen the project. According to Microsoft Learn, in-session reload is a **preview** feature: it requires the August 2026 release or later and the **Detect and reload external PBIP changes** option under **File > Options and settings > Options > Preview features**, followed by a restart. Unsaved Desktop changes can be discarded when you reload.
4. Verify the change in Desktop. Check affected pages, visuals, filters, or measures before saving or publishing. For query changes, also verify that the data refresh succeeds.

## Microsoft Learn references

- [Power BI Desktop projects (PBIP)](https://learn.microsoft.com/en-us/power-bi/developer/projects/projects-overview) — project structure, opening and publishing projects, and limitations.
- [Edit PBIP files outside Power BI Desktop](https://learn.microsoft.com/en-us/power-bi/developer/projects/projects-external-editing) — VS Code workflow, reload prerequisites, and conflict handling.
- [Power BI Desktop project report folder](https://learn.microsoft.com/en-us/power-bi/developer/projects/projects-report#pbir-folder-and-files) — PBIR file structure, per-file schemas, and the difference from PBIR-Legacy.
- [Power BI Desktop project semantic model folder](https://learn.microsoft.com/en-us/power-bi/developer/projects/projects-dataset) — TMDL, the local data cache, and pending Power Query changes.
- [Power BI implementation planning: Develop content and manage changes](https://learn.microsoft.com/en-us/power-bi/guidance/powerbi-implementation-planning-content-lifecycle-management-develop-manage) — choosing a file format and managing changes.

## Three small edits to try in VS Code

Save any pending work in Power BI Desktop before you start. Try one example at a time: save the file in VS Code, then select **Apply external changes** in Power BI Desktop or close and reopen the project. The diffs below show only the line to replace, not the entire file.

### 1. Rename the Sales Overview page

Open [page.json](<./30-Starter-Sales Analysis - Copy.Report/definition/pages/30a1b2c3d4e5f6a7b8c9/page.json>). Change only `displayName`; leave `name` and the folder name unchanged.

```diff
-  "displayName": "Sales Overview",
+  "displayName": "Sales Summary",
```

**Check in Desktop:** The page tab now reads **Sales Summary**. The page itself has the same visuals.

Microsoft Learn: [PBIR folder and files](https://learn.microsoft.com/en-us/power-bi/developer/projects/projects-report#pbir-folder-and-files).

### 2. Move the Total Sales card to the right

Open the card's [visual.json](<./30-Starter-Sales Analysis - Copy.Report/definition/pages/30a1b2c3d4e5f6a7b8c9/visuals/totalSalesCard01/visual.json>). In the `position` object, change only `x`.

```diff
-    "x": 50,
+    "x": 75,
```

**Check in Desktop:** The card is 25 canvas units farther to the right and stays at the same height and size. Its measure binding is unchanged.

Microsoft Learn: [PBIR folder and files](https://learn.microsoft.com/en-us/power-bi/developer/projects/projects-report#pbir-folder-and-files) and [external changes to PBIR files](https://learn.microsoft.com/en-us/power-bi/developer/projects/projects-report#external-changes-to-pbir-files).

### 3. Display Total Sales without decimal places

Open [Sales.tmdl](<./30-Starter-Sales Analysis - Copy.SemanticModel/definition/tables/Sales.tmdl>). Under `measure 'Total Sales'`, change only the `formatString` value and keep the existing indentation.

```diff
-formatString: \$#,0.00;(\$#,0.00);\$#,0.00
+formatString: \$#,0;(\$#,0);\$#,0
```

**Check in Desktop:** In a visual that uses the model's format, a value such as `$1,234.56` displays as `$1,235` with US English formatting and display units set to **None**. The DAX formula and underlying numeric value are unchanged. Visual-level formatting can override the model format.

Microsoft Learn: [Make external changes to TMDL files](https://learn.microsoft.com/en-us/power-bi/developer/projects/projects-dataset#make-external-changes-to-tmdl-files) and [TMDL syntax](https://learn.microsoft.com/en-us/analysis-services/tmdl/tmdl-overview).
