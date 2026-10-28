---
title: "Kate Daudy: Artist Website"
excerpt: "Classifying an artist's whole body of work, and an easy way for her to upload new pieces · Framer, WordPress, JavaScript"
collection: portfolio
type: websites
order: 2
---

*Client website · Jul 2025 – Nov 2025 · Framer, WordPress (custom post types, Advanced Custom Fields, WP All Import), JavaScript, REST API · [katedaudy.com](https://katedaudy.com)*

<!-- PICTURE: the live Works page on katedaudy.com, next to the upload form -->

## What it is

The website for the artist Kate Daudy. The site itself ended up being built in Framer; the main job was working out how to classify her whole body of work, and giving her an easy way to add new pieces herself.

## Classifying the work

* **Three types of entry:** works, exhibitions, and media (talks, podcasts and films). These are the live site's Works, Exhibitions and Media & Press sections.
* **Tags for browsing:** every work is tagged by year, by medium (textiles, sculpture, publications, fragrances, performance, maps, interventions, digital and experimental) and by body of work (such as *Superbloom* and *Wonderchaos*). A work can have several mediums.
* **Cataloguing:** I turned this into a spreadsheet template with one sheet per type of entry, and columns for title, year, dates, medium, body of work, description, captions, images and files, plus a notes column for questions to me. Kate filled it in, and the sheets were bulk-imported into a WordPress back end with custom content types and fields.

## Uploading new work

A single-page upload tool, so Kate can add entries without learning the CMS:

* She signs in with a WordPress application password, picks the type of entry and fills in one form: title, dates, description, cover image, gallery, tags, and links or video.
* Images go to the media library, and the entry is created as a draft through a custom REST endpoint, ready for her to check and publish.
* The form saves itself as she types, warns if an entry with the same title already exists, and shows which tags are already in use and which are new, so the classification stays consistent.
* It came with a written guide for Kate (publishing drafts, and adding images, links and tags to existing entries), updated as she asked questions.
