# Frescopa Site Project

This is the `LucianRadu/frescopa` copy of the AEM Authoring with Edge Delivery Services demo.

## Edit and publish content

- **Author:** [AEM Sites → Frescopa → English](https://author-p226372-e2311735.adobeaemcloud.com/ui#/aem/sites.html/content/frescopa/en). Editable pages live in AEM under `/content/frescopa/en`; `index` is the homepage, `nav` is the shared header, and `footer` is the shared footer. Images and other assets live in AEM Assets under `/content/dam/frescopa`.
- **Preview:** https://main--frescopa--lucianradu.aem.page/
- **Live:** https://main--frescopa--lucianradu.aem.live/

1. In AEM Sites, select an existing page and click **Edit** to open Universal Editor. To add a page, open the intended parent folder and choose **Create → Page**. Use the same template as comparable Frescopa pages, give the page a URL-friendly name, then open it in Universal Editor. Upload images to the Frescopa folder in AEM Assets and select them in the editor.
2. In Universal Editor, select **Publish → Preview**. Check the actual `.aem.page` URL and verify that the page, assets, and links work. Use [the path mappings](paths.json) to find the delivery URL: for example, `/content/frescopa/en/coffee` becomes `/coffee`, and `index` becomes `/`. To surface a new page in the main navigation, edit and publish `nav` too.
3. When the content is ready to go public, select **Publish → Live** in Universal Editor. Verify the same path on `.aem.live`. The classic dev Publish hostname (`publish-p226372-e2311735.adobeaemcloud.com`) is separate and is not the EDS Live destination.

## Edit code and static files

This repository holds the site code (blocks, scripts, styles), [`paths.json`](paths.json), and static files such as [`.well-known/poppy.json`](.well-known/poppy.json). Authored pages do not live in Git. [AEM Code Sync](https://github.com/apps/aem-code-sync) deploys code changes; verify a feature branch at `https://{branch}--frescopa--lucianradu.aem.page/` before merging to `main`. For the Poppy manifest, check the [exact Live URL](https://main--frescopa--lucianradu.aem.live/.well-known/poppy.json) after Code Sync; it is not published from Universal Editor.

## Check the connection if publishing fails

In AEM Author, open **Tools → Cloud Services → Edge Delivery Services Configuration → frescopa**. The target should be **`lucianradu/frescopa`**, branch **`main`**. The content source is configured in the EDS Configuration Service, not in `fstab.yaml`:

```text
https://author-p226372-e2311735.adobeaemcloud.com/bin/franklin.delivery/lucianradu/frescopa/main
```

If AEM reports missing permissions, compare the ID on the configuration’s **Authentication** tab with the technical account in [EDS User Admin](https://tools.aem.live/tools/user-admin/index.html). It should have **Config Admin** on the `lucianradu/frescopa` site; that role already includes Publish. For setup details, see the [Universal Editor developer tutorial](https://www.aem.live/developer/ue-tutorial).
