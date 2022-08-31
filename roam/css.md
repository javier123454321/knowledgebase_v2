- [[javier-theme]]
    - ```css
/****************************
General
*****************************/

.roam-block, 
.rm-block-input .rm-block-text .dont-unfocus-block, 
textarea{
  font-weight: 400;
}
textarea{
  background-color: [[F0F0EB]];
  padding: .2em;
  font-weight: 500;
}
h1, .rm-title-textarea{
  font-family: 'Bree Serif', serif;
  font-weight: 800;
}
.rm-title-textarea{
  transition-duration: .2s;
  background-color: [[F8F8F9]];
 }

.rm-block-text{
  max-width: 800px;
}
strong > span{
  font-weight:700 !important;
}

/****************************
Sidebar
*****************************/
.roam-body .roam-app .roam-sidebar-container 
.roam-sidebar-content .rm-db-title {
  transition-duration: .3s;
  color: [[B39685]];
}
/* Graph Title Container */
.roam-body .roam-app .roam-sidebar-container .roam-sidebar-content .top-row:hover {
  background-color:[[DFDCD9]];
}
.roam-body .roam-app .roam-sidebar-container .roam-sidebar-content .top-row:hover > * {
  color: [[F5F8FA]];
}
.roam-body .roam-app .roam-sidebar-container {
  background-color: [[F6F5F2]];
   box-shadow: 6px 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
  
}
.roam-body .roam-app .roam-sidebar-container .roam-sidebar-content .log-button {
  color: [[B39685]];
}
.roam-body .roam-app .roam-sidebar-container
.roam-sidebar-content .starred-pages-wrapper {
  color: [[B39685]];
}

.roam-body .roam-app .roam-sidebar-container
.roam-sidebar-content .starred-pages-wrapper:hover{
  padding-left: 8px;
  transition-duration: .3s;
  color: [[B39685]];
}
.roam-body .roam-app .roam-sidebar-container .roam-sidebar-content 
.starred-pages-wrapper .starred-pages .page {
  padding-left: 8px;
  transition-duration: .3s;
  color: [[B39685]];
}
.roam-body .roam-app .roam-sidebar-container .roam-sidebar-content 
.starred-pages-wrapper .starred-pages .page:hover, div.log-button:hover{
    padding-left: 3px;
    background-color: [[DFDCD9]];
 }
.roam-body .roam-app .roam-sidebar-container .roam-sidebar-content .log-button:hover{
 	background-color: [[C4BFA6]];
    transition-duration: .2s;
 }

.rm-title-display{
  font-weight: bold;
}

[[right-sidebar]]{
  background-color: [[F0EEEA]];
  box-shadow: inset 4px 4px 4px 0 rgba(0, 0, 0, 0.06);
}
/****************************
Background
*****************************/

.roam-toolkit--panel{
  background-color: [[F6F7F9]];
}

/****************************
Top Bar
*****************************/
.roam-topbar{
  background-color: [[CABC9C]];
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
}

/****************************
Aliases and Block Refs
*****************************/

.rm-page-ref-link-color{
	color: #756602;
}

.rm-ref-page-view-title a{
	color: #756602;  
}
a.rm-alias.rm-alias-page{
	color: #756602 !important;  
}

.rm-alias.rm-alias-external{
	color: [[685C0B]] !important;
  	text-decoration: underline;
}
.rm-alias:hover.rm-alias-external:hover{
  	background-color: [[EEEAE0]];
	color: [[685C0B]] !important;
  	text-decoration: underline;
}

.rm-block-ref {
  border-color: [[F0EBA8]];
}
.rm-block-ref:hover {
  transition-duration .3s;
  background-color: rgba(0,0,0,0);
  border-color:rgba(0,0,0,0);
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
}
.rm-block-ref:active {
    box-shadow: inset 0 4px 6px -1px rgba(0, 0, 0, 0.1), inset 0 2px 4px -1px rgba(0, 0, 0, 0.06);
}

/*** Block Embed ***/
.rm-hide-bullet > .rm-embed-inner-block-hide:hover .rm-embed-margin-action:hover{
	background: linear-gradient(90deg, rgb(180,194,199) 0%, rgba(255,255,255,0) 88%);
}
.rm-embed-margin-action {
	background: linear-gradient(90deg, rgb(190,201,204) 0%, rgba(255,255,255,0) 50%);
  	border: none;
}

.check-container input:checked ~ .checkmark {
    background-color: [[EAC640]];
}
```
