---
title: About us
keywords: homepage documentation docs
tags: [getting_started]
sidebar: myd	oc_sidebar
permalink: index.html
summary: This is the go-to guide on asking questions and sharing data cards using Askdata. You’ll learn in depth about how questions are expressed, how to chart data cards, as well as how to share data cards and create feeds.
---

## About

Askdata's mission is to make data productive for everyone.

### Motivation

Data fuels powerful insights and changes lives.

## Our Culture

The culture of any organization flows from its people, so we seek out teammates who share our values and drive, not people who are exactly like us. We’ve built a company that allows everyone to take risks and thrive professionally — without ever hiding their authentic selves.

<style>
	:root {
  --gutter: 20px;
}

.app {
  padding: var(--gutter) 0;
  display: grid;
  grid-gap: var(--gutter) 0;
  grid-template-columns: var(--gutter) 1fr var(--gutter);
  align-content: start;
}

.app > * {
  grid-column: 2 / -2;
}

.app > .full {
  grid-column: 1 / -1;
}

.hs {
  display: grid;
  grid-gap: calc(var(--gutter) / 2);
  grid-template-columns: 10px;
  grid-template-rows: minmax(150px, 1fr);
  grid-auto-flow: column;
  grid-auto-columns: calc(50% - var(--gutter) * 2);

  overflow-x: scroll;
  scroll-snap-type: x proximity;
  padding-bottom: calc(.75 * var(--gutter));
  margin-bottom: calc(-.25 * var(--gutter));
}

.hs:before,
.hs:after {
  content: '';
  width: 10px;
}


/* Demo styles */

html,
body {
  height: 100%;
}

body {
  display: grid;
  place-items: center;
  background: #456173;
}

ul {
  list-style: none;
  padding: 0;
}

h1,
h2,
h3 {
  margin: 0;
}

.app {
  width: 375px;
  height: 667px;
  background: #DBD0BC;
  overflow-y: scroll;
}

.hs > li,
.item {
  scroll-snap-align: center;
  padding: calc(var(--gutter) / 2 * 1.5);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background: #fff;
  border-radius: 8px;
}

.no-scrollbar {
  scrollbar-width: none;
  margin-bottom: 0;
  padding-bottom: 0;
}
.no-scrollbar::-webkit-scrollbar {
  display: none;
}
</style>

<div class="app">
  <h1>Some headline</h1>
  
  <ul class="hs full">
    <li class="item">test</li>
    <li class="item">test</li>
    <li class="item">test</li>
    <li class="item">test</li>
    <li class="item">test</li>
    <li class="item">test</li>
  </ul>
  
  <ul class="hs full no-scrollbar">
    <li class="item">test</li>
    <li class="item">test</li>
    <li class="item">test</li>
    <li class="item">test</li>
  </ul>
  
  <div class="container">
    <div class="item">
      <h3>Block for context</h3>
    </div>
  </div>
</div>

<img src="/media/product/askdata-search-insights.gif" class="mx-auto d-block" style="max-width:90%">

## Our Values

Our core values make us who we are — and explain why Askdata is such a great place to work. We’re committed to upholding our values no matter how much we grow, or how fast.

## Our Story

Established out of Y Combinator in 2019, Askdata began with a realization: For modern companies using traditional BI tools badly underperformed. So we designed an entirely new kind of data experience.