<%*
const title = await tp.system.prompt("Documentation post title");
if (!title) { return; }

const slug = title
  .toLowerCase()
  .replace(/['"`’‘“”]/g, "")
  .replace(/[^a-z0-9]+/g, "-")
  .replace(/^-+|-+$/g, "");

const date = tp.date.now("YYYY-MM-DD");
const basePath = app.vault.getAbstractFileByPath("bb-docs/_posts") ? "bb-docs/" : "";
await tp.file.move(`${basePath}_posts/${date}-${slug}`);
-%>
---
layout: post
title: <% title %>
date: <% tp.date.now("YYYY-MM-DD") %>
author: Brad Barrish
description: 
ogimage: opengraphimage.jpeg
---

