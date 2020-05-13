# facebook-dark-mode
Just add this script to Tempermonkey extension.
It's a bit bugged but you can fast change everything you need.

```javascript
// ==UserScript==
// @name         Facebook dark mode
// @namespace    https://github.com/FedericoHeichou/facebook-dark-mode/
// @version      0.1
// @description  Add CSS style to activate Facebook dark mode
// @author       FedericoHeichou
// @match        https://www.facebook.com/*
// @grant        none
// ==/UserScript==

function addStyle(styles) {
    /* Create style document */
    var css = document.createElement('style');
    css.type = 'text/css';
    if (css.styleSheet) {
        css.styleSheet.cssText = styles;
    } else {
        css.appendChild(document.createTextNode(styles));
    }
    /* Append style to the tag name */
    document.getElementsByTagName("head")[0].appendChild(css);
}

(function() {
    'use strict';
    var colors = {
        "header": "#2e2e2e",
        "header_text": "#ffffff",
        "theme": "#0f0f0f",
        "inner_boxes": "#2e2e2e",
        "heading_and_links": "#ffffff",
        "text": "#ffffff",
        "buttons": "#5c5c5c",
        "borders": "#5c5c5c",
    };
    var styles = `/*cssv_borders_color*/
    *:not(a):not(button), #mainContainer *:not(a):not(button)::before, ._69pt, .fbNubButton {
        border-color: ` + colors.borders + ` !important
    }
    ._69pt, .fbNubButton {
        border: 1px solid !important;
    }

    /*cssv_header_color*/
    ._4f7n, ._2s1x ._2s1y, ._53jh, #fbTimelineHeadline, ._83k {
        background: ` + colors.header + ` !important;
        border-color: #252525 !important
    }

    ._4f7n:after {
        background: none !important;
    }

    ._53jh input, ._585-, #fbTimelineHeadline, ._6-6 {
        border-color: #252525 !important
    }

    ._4kny .uiToggle:not(.hasNew) ._2n_9, ._4d1i ._59fb, ._5lxt {
        filter: invert(1)
    }

    /*cssv_theme_color*/
    body, .fbNubFlyoutFooter, div#globalContainer, #mainContainer, #leftCol, #facebook, #contentCol, #pageFooter, .fbChatSidebar, ._juy, .oh7imozk, ._19bs:hover,
    /*likes popup*/
    div._4-i2,
    /*mutal friend pop */
    ._4-i0, ._iw3, ._cue, .fbNubFlyoutTitlebar, .pagesTimelineLayout #globalContainer,
    /*msg recv*/
    ._1nc7 ._5w1r {
        background: ` + colors.theme + ` !important;
    }

    ._ipo, ._1g5v+._4arz, #rightColContent ul {
        background: none;
         !important
    }

    .sideNavItem *::after, .sideNavItem a {
        background: transparent !important;
        border-color: transparent !important;
    }

    .fbSettingsList a:hover, .sideNavItem a:hover, .fbxWelcomeBoxSmallRow:hover::after {
        background: rgba(0, 0, 0, 0.1) !important;
        border-color: transparent !important;
    }

    #globalContainer, .fbIndex .gradient, ._4lh .fbTimelineTimePeriod, .loadingIndicator, ._41nt {
        background: ` + colors.theme + ` !important;
    }

    /*cssv_buttons_color*/
    ._4po5 div {
        background-color: ` + colors.buttons + ` !important;
    }
    div._4kf5, div._1aa6, div._4gx_, div._4k7e, div._1aa6 div, ._5w-5, ._4kf5, span._3dlh {
        background-color: ` + colors.inner_boxes + ` !important;
    }
    ._5w1r {
        border-radius: 20px;
        border-bottom-left-radius: 20px;
    }
    ._42fu, ._xag, ._3z5 ._3zr a, .uiButtonConfirm, ._xah, ._4jy1, ._517h, ._59pe, ._4jy2, ._3g_v, .uiButton, .uiButtonSuppressed, ._43rm, .hybvsw6c, ._271k, ._51lp, ._58al, ._3rhb {
        background: ` + colors.buttons + ` !important;
        border-color: #4a4a4a !important
    }

    ._xag:hover, ._3z5 ._3zr a:hover, .uiButtonConfirm:hover, ._xah:hover, ._4jy1:hover, ._517h:hover, ._59pe:hover, ._4jy2:hover, ._3g_v:hover, .uiButton:hover, .uiButtonSuppressed:hover {
        background: #4a4a4a !important
    }

    /*cssv_text_color*/
    blockquote div._pyf {
        background: ` + colors.text + ` !important;
    }
    *, ._1nd3 a, .snippet span, li._kv ._l3, ._1n-e, ._c24, .fcg, .sideNavItem a, ._585_ {
        color: ` + colors.text + ` !important;
    }

    /*cssv_text_header_color*/
    ._2s25, ._2s25 span, ._6-6, ._6-6 span, ._8_2 span, ._9ry {
        color: ` + colors.header_text + ` !important;
    }

    /*cssv_heading_color*/
    .ellipsis, ._3na7 ._4jy1, ._3na7 ._4jy2, a, .name, .name span, a span, a .accessible_elem, a ._l1, ._3s6x, .__MenuItem span, .__MenuItem div, ._5vb_, ._5vb_ #contentCol, ._5qtp, button, button span, ._5p3y .uiSideNav .item div, .uiButton input, label, label span, ._585_ {
        color: ` + colors.heading_and_links + ` !important;
    }

    /*cssv_inner_boxes_color*/
    .tooltipContent, ._4arz span, ._t, .fbFeedTicker .fbFeedTickerStory, ._3soe, ._4-u8, .commentable_item, #globalContainer, html ._262m ._698, ._5vsj._5vsj._5vsj, ._5vsj .UFIRow, ._6m2, ._30f, ._1lot, #fbContextualHelpContent div, .pbs, .uiBoxWhite, .uiBoxLightblue, .uiScrollableAreaBody, .uiToggleFlyout, ._30d, .escapeHatchMinimal, .fbNubButton, ._53ij, .conversationContainer, .fbChatTypeahead ._4p-s, ._7a5, #documentation_body_pagelet td, .uiMenu, ._4t2a, ._3t09, ._69pt,  ._21r, ._3zsi {
        background: ` + colors.inner_boxes + ` !important;
    }

    .uiTypeahead, ._585-, ._5vb_ .home_right_column .fbFeedTicker .tickerStoryActive, ._5vb_ .home_right_column .fbFeedTicker .tickerStoryClickable:hover, ._1lor, ._kj3, .fbTimelineStickyHeader *, ._54ng, ._5i-7, ._3ubp, ._1cx1 ._ei_, ._3cz, ._g3h, ._1a8t, ._1xy2, ._5wcf, ._1nc6 ._d97, ._hh7, .uiBoxGray, ._344_, ._3iue, #documentation_body_pagelet th, ._25_a:hover, ._25_c, html ._55r1, ._6-7:hover, ._6-6:hover, ._9rx.openToggler, ._9ry:hover, ._33e, ._54ne, ._54ne a, ._55ln:hover {
        background: #242424 !important;
        background-color: #242424 !important;
    }

    .uiToggleFlyout *:not(button):not(._517h), .uiToggleFlyout *:not(button):not(._517h):hover, .mtm *, ._3ztw:hover, ._3ztw a {
        background-color: transparent !important;
    }

    ._2iwq, ._2iwq div, ._2iwq::before, ._sg1, ._5mac, ._3t3, ._3ow-, ._1_cb, ._4sp8, .displayedTickerToggleWrapper .tickerLineToggle {
        background: transparent !important
    }

    .UFICommentPhotoIcon, .UFICommentStickerIcon {
        filter: invert(1)
    }

    .uiScrollableAreaBody a {
        border-color: transparent !important
    }

    ._3c40, ._57d8, ._1jyk, .commentable_item *, ._4-h7:hover, ._19_3, div._5a8u, ._4o-g:hover {
        background-color: transparent !important
    }

    ._6lh ._6li, .UFIInputContainer, ._m_1, ._70l {
        background: rgba(0, 0, 0, 0.1) !important
    }

    ._558b ._54nc, .uiMenuItem .itemAnchor, ._s39 {
        border: none !important
    }

    input, ._55r1, .fbChatSidebarMessage {
        background: #242424
    }

    .tooltipContent {
        border: 1px solid rgba(100, 100, 100, .4);
        box-shadow: 0 3px 8px rgba(0, 0, 0, .25)
    }`;
    addStyle(styles)
})();
```
