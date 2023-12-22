# Firefox-esr 115.0 Tree Style Tab + Rainbow Hostnames

1. Navigate to about:config in Firefox (accept risk and continue through the *scary* warning if it is your 1st time opening about:config)

2. Set boolean toolkit.legacyUserProfileCustomizations.stylesheet to "True"

3. Navigate to about:profiles and locate your default profile path (in the author's case debian environment): `/home/user/.mozilla/firefox/r4nd0m.im-a-default-profile`

4. Change directories to said profile root:
```bash
user@kali:~/.mozilla/firefox/r4nd0m.im-a-default-profile$ 
```

5. Make a directory called "chrome" and touch an empty file called userChrome.css:
```bash
user@kali:~/.mozilla/firefox/r4nd0m.im-a-default-profile$ mkdir chrome && touch chrome/userChrome.css
```
6. Using $EDITOR of your choice (vim) populate userChrome.css:
```css
#sidebar-box[sidebarcommand="treestyletab_piro_sakura_ne_jp-sidebar-action"] #sidebar-header {
  display: none;
}
#main-window[tabsintitlebar="true"]:not([extradragspace="true"]) #TabsToolbar > .toolbar-items {
  opacity: 0;
  pointer-events: none;
}
#main-window:not([tabsintitlebar="true"]) #TabsToolbar {
    visibility: collapse !important;
}
/* Shrink sidebar until hovered, when using Tree Style Tab. */
:root {
	--thin-tab-width: 30px;
	--wide-tab-width: 200px;
}
/* Hide splitter, when using Tree Style Tab. */
#sidebar-box[sidebarcommand="treestyletab_piro_sakura_ne_jp-sidebar-action"] + #sidebar-splitter {
	display: none !important;
}
/* Sidebar min and max width removal */
#sidebar {
	max-width: none !important;
	min-width: 0px !important;
}
#sidebar-box:not([sidebarcommand="treestyletab_piro_sakura_ne_jp-sidebar-action"]) {
	min-width: var(--wide-tab-width) !important;
	max-width: none !important;
}
#sidebar-box[sidebarcommand="treestyletab_piro_sakura_ne_jp-sidebar-action"] {
	position: relative !important;
	transition: all 300ms !important;
	min-width: var(--thin-tab-width) !important;
	max-width: var(--thin-tab-width) !important;
}
#sidebar-box[sidebarcommand="treestyletab_piro_sakura_ne_jp-sidebar-action"]:hover {
	transition: all 300ms !important;
	min-width: var(--wide-tab-width) !important;
	max-width: var(--wide-tab-width) !important;

	/* Negative right-margin to keep page from being pushed to the side. */
	margin-right: calc((var(--wide-tab-width) - var(--thin-tab-width)) * -1) !important;
}
```
7. Navigate to about:addons and install 2 FF extensions. Namely Tree Style Tab and TST Colored Tabs (unsolicited author advise: advisable to look over the source and/or grab from Github and give the code an ocular patdown for anything glaringly malicious/obviously nefarious as benign plugins can become hijacked or else go "rogue" from time-to-time): 
    Tree Style Tabs: https://addons.mozilla.org/en-US/firefox/addon/tree-style-tab/?utm_source=addons.mozilla.org&utm_medium=referral&utm_content=search
    Tree Style Tabs Source: https://github.com/piroor/treestyletab/blob/master/README.md
    

    TST Colored Tabs: https://addons.mozilla.org/en-US/firefox/addon/tst-colored-tabs/?utm_source=addons.mozilla.org&utm_medium=referral&utm_content=search
    https://addons.mozilla.org/en-US/firefox/addon/tree-style-tab/?utm_source=addons.mozilla.org&utm_medium=referral&utm_content=search
    TST Colored Tabs Source: https://github.com/MurzNN/TST-Colored-tabs
    
8. In about:addons Click on Tree Style Tab. Heres where it gets fun! Personalize to your liking! (https://github.com/piroor/treestyletab/wiki/Code-snippets-for-custom-style-rules#for-version-2x)
    Under Preferences -> Extra Style Rules
```css
--theme-colors-frame: #1c1b22​;
--theme-colors-icons: rgb(251,251,254)​;
--theme-colors-ntp_background: rgb(43, 42, 51)​;
--theme-colors-ntp_card_background: rgb(66,65,77)​;
--theme-colors-ntp_text: rgb(251, 251, 254)​;
--theme-colors-popup: rgb(66,65,77)​;
--theme-colors-popup_border: rgb(82,82,94)​;
--theme-colors-popup_highlight: rgb(43,42,51)​;
--theme-colors-popup_text: rgb(251,251,254)​;
--theme-colors-sidebar: #38383D​;
--theme-colors-sidebar_border: rgba(255, 255, 255, 0.1)​;
--theme-colors-sidebar_text: rgb(249, 249, 250)​;
--theme-colors-tab_background_text: #fbfbfe​;
--theme-colors-tab_line: transparent;
--theme-colors-tab_selected: rgb(66,65,77)​;
--theme-colors-tab_text: rgb(251,251,254)​;
--theme-colors-toolbar: rgb(43,42,51)​;
--theme-colors-toolbar_bottom_separator: hsl(240, 5%, 5%)​;
--theme-colors-toolbar_field: rgb(28,27,34)​;
--theme-colors-toolbar_field_border: transparent;
--theme-colors-toolbar_field_focus: rgb(66,65,77)​;
--theme-colors-toolbar_field_text: rgb(251,251,254)​;
--theme-colors-toolbar_text: rgb(251, 251, 254)​;
--theme-colors-toolbar_top_separator: transparent;
--theme-colors-button: rgb(43,42,51)​;
--theme-colors-button_hover: rgb(82,82,94)​;
--theme-colors-button_active: rgb(91,91,102)​;
--theme-colors-button_primary: rgb(0, 221, 255)​;
--theme-colors-button_primary_hover: rgb(128, 235, 255)​;
--theme-colors-button_primary_active: rgb(170, 242, 255)​;
--theme-colors-button_primary_color: rgb(43, 42, 51)​;
--theme-colors-input_background: #42414D​;
--theme-colors-input_color: rgb(251,251,254)​;
--theme-colors-input_border: #8f8f9d​;
--theme-colors-autocomplete_popup_separator: rgb(82,82,94)​;
--theme-colors-appmenu_update_icon_color: #54FFBD​;
--theme-colors-appmenu_info_icon_color: #80EBFF​;
--theme-colors-tab_icon_overlay_stroke: rgb(66,65,77)​;
--theme-colors-tab_icon_overlay_fill: rgb(251,251,254)​;
--theme-properties-color_scheme: dark;
--theme-properties-panel_hover: color-mix(in srgb, currentColor 9%, transparent);
--theme-properties-panel_active: color-mix(in srgb, currentColor 14%, transparent);
--theme-properties-panel_active_darker: color-mix(in srgb, currentColor 25%, transparent);
--theme-properties-toolbar_field_icon_opacity: 1;
--theme-properties-zap_gradient: linear-gradient(90deg, #9059FF​ 0%, #FF4AA2​ 52.08%, #FFBD4F​ 100%);
```
Directly under Extra Style Rules (after some opacity related blurb:
```css
/* Show title of unread tabs with red and italic font */
/*
:root.sidebar tab-item.unread .label-content {
  color: red !important;
  font-style: italic !important;
}
*/

/* Add private browsing indicator per tab */
/*
:root.sidebar tab-item.private-browsing tab-label:before {
  content: "🕶";
}
*/
/* Hide .twisty and adjust margins so favicons have 7px on left. */
.tab .twisty {
	visibility: hidden;
	margin-left: -12px;
}

/* Push tab labels slightly to the right so they're completely hidden in collapsed state */
.tab .label {
	margin-left: 7px;
}

/* Hide close buttons on tabs. */
.tab .closebox {
	visibility: collapse;
}

/* Hide sound playing/muted button. */
.sound-button::before {
	display: none !important;
}

/* Hide 'new tab' button. */
.newtab-button {
	display: none;
}

/* ################################################ */
/* ##### COLOR THEME ############################## */
/* ################################################ */
@keyframes spin {
	0% {
		transform: rotate(0deg);
	}
	100% {
		transform: rotate(360deg);
	}
}
@keyframes pulse {
	0% {
		width: 0px;
		height: 0px;
		opacity: 1;
	}
	100% {
		width: 350px;
		height: 350px;
		opacity: 0;
		top: calc(50% - 175px);
		left: calc(50% - 175px);
	}
}
:root {
	background-color: #383838;
}
#tabbar {
	border-right: 1px solid #1d1d1d;
	box-shadow: none !important;
}
.tab {
	background-color: transparent;
	border-color: #292929;
	color: rgba(207,207,207,0.75);
	box-shadow: none !important;
}
.tab:hover {
	background-color: #404040 !important;
	color: rgba(207,207,207,1) !important;
}
.tab.discarded {
	background-color: #1d1d1d;
	color: #383838 !important;
}
.tab.discarded:hover {
	background-color: #292929 !important;
}

.tab.active {
	background-color: #8fa876;
}
.tab.active:hover {
	background-color: #8fa876 !important;
}


/* Adjust style for tab that has sound playing. */
.tab.sound-playing .favicon::after {
	content: '';
	position: absolute;
	top: 50%;
	left: 50%;
	border-radius: 50%;
	background: #FFFFFF;
	animation: pulse 2s ease-out 0s infinite;
	z-index: -1;
	opacity: 0;
}

/* Adjust style for tab that is muted. */
.tab.muted {
	opacity: 0.5;
}
#tabbar { 
  overflow-x: hidden;
}
#tabbar { scrollbar-width: none; }
```
