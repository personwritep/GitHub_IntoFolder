// ==UserScript==
// @name        GitHub IntoFolder 🔵
// @namespace        http://tampermonkey.net/
// @version        0.2
// @description        ファイルのフォルダー整理を補助する　「Shift+右Click」
// @author        personwritep
// @match        https://github.com/*
// @icon        https://www.google.com/s2/favicons?sz=64&domain=github.com
// @grant        none
// @updateURL        https://github.com/personwritep/GitHub_IntoFolder/raw/main/GitHub_IntoFolder.user.js
// @downloadURL        https://github.com/personwritep/GitHub_IntoFolder/raw/main/GitHub_IntoFolder.user.js
// ==/UserScript==

let folder_name; // フォルダー名
let set_ver; // フォルダーの連番

let lastUrl=location.href;
let observer=new MutationObserver(()=>{
    let currentUrl=location.href;
    if(currentUrl !==lastUrl){
        lastUrl=currentUrl;
        main(); }});

observer.observe(document.body, { childList: true, subtree: true });

main();

function main(){
    if(isRepoRoot()){
        set_folder();
        to_edit(); }
    else if(isEdit() || isnewEditor()){
        set_folder();
        let q=window.location.search;
        if(q.includes('GIH') && !q.includes('search')){ // クエリ文字列「GIH」で起動
            setTimeout(()=>{
                input_filename();
            }, 800); }}
    else{
        rem_panel(); }


    function isRepoRoot(){ // リポジトリのルート画面の判定
        let pathParts=window.location.pathname.split('/').filter(Boolean);
        return pathParts.length===2 || (pathParts.length>=4 && pathParts[2]==='tree'); }

    function isEdit(){ // 既存ファイルの編集画面の判定
        let pathParts=window.location.pathname.split('/').filter(Boolean);
        return pathParts.length>= 4 && pathParts[2]==='edit'; }

    function isnewEditor(){ // 新規ファイルの作成画面の判定
        let pathParts=window.location.pathname.split('/').filter(Boolean);
        return pathParts.length>=3 && pathParts[2]==='new'; }

} // main()



function rem_panel(){
    document.querySelector('#folder_panel') ?.remove(); }



function set_folder(){
    let panel=
        '<div id="folder_panel">'+
        'folder: <input class="f_name" type="text">'+
        '+<input class="ver_num" type="number" min="-1" step="1">'+
        '<style>'+
        '#folder_panel { position: fixed; top: 17px; left: 410px; z-index: 100; '+
        'padding: 3px 6px; border-radius: 6px; color: #fff; background: red; '+
        'font: normal 16px/22px Meiryo; } '+

        '.f_name { width: 120px; padding: 2px 2px 0px 4px; '+
        'border: 1px solid #ccc; border-radius: 3px; outline: none !important; } '+

        '.ver_num { width: 48px; padding: 2px 2px 0px 4px; text-align: center; '+
        'border: 1px solid #ccc; border-radius: 3px; outline: none !important; } '+
        'input[type=number].ver_num::-webkit-inner-spin-button { '+
        'height: 16px; margin-top: 2px; appearance: auto; } '+
        '</style></div>';

    if(!document.querySelector('#folder_panel')){
        document.body.insertAdjacentHTML('beforeend', panel); }


    folder_name=localStorage.getItem("GOV_name");
    if(!folder_name){
        folder_name='folder'; }
    localStorage.setItem("GOV_name", folder_name);

    let f_name=document.querySelector('#folder_panel .f_name');
    if(f_name){
        f_name.value=folder_name; }

    f_name.onchange=()=>{
        let val=f_name.value;
        if(val==='' || /\s/.test(val)){
            alert("空白文字の入力や入力が無い状態です \n"+
                  "入力を初期値の folder にリセットします");
            val='folder';
            f_name.value=val; }
        localStorage.setItem("GOV_name", val); }


    set_ver=localStorage.getItem("GOV_ver");
    if(set_ver===null || set_ver<-1){
        set_ver=-1; }
    localStorage.setItem("GOV_ver", set_ver);

    let ver_num=document.querySelector('#folder_panel .ver_num');
    if(ver_num){
        ver_num.value=set_ver; }

    ver_num.oninput=()=>{
        localStorage.setItem("GOV_ver", ver_num.value); }

} // set_folder()



function to_edit(){
    document.addEventListener('contextmenu', (event)=>{
        let row=event.target.closest('.react-directory-row');
        if(!row){
            return; }
        event.preventDefault();
        event.stopPropagation();
        into_folder(row, event);
    }, true);


    function into_folder(row, event){
        if(event.shiftKey){ // ファイルリストのファイル名を「Shift+右Click」
            event.preventDefault();
            event.stopImmediatePropagation();
            let svg=row.querySelector('svg.octicon-file');
            if(svg){ // ファイル名の行の場合
                let link=row.querySelector('.react-directory-filename-cell a');
                if(link){
                    if(check_js(link)){ //「～.user.js」「～index.html」のファイルは除外
                        let file_name=link.textContent;
                        if(!file_name){
                            alert("ファイル名が取得できません"); }
                        else{
                            let root; // リポジトリルートのURL
                            let edit_url;
                            let now_url=location.href.split('?')[0];
                            if(now_url.includes('/tree/main')){
                                root=now_url.replace('/tree/main', ''); }
                            else{
                                root=now_url; }

                            edit_url=root +'/edit/main/'+ file_name +'?GIH'; // クエリ「GIH」を設定
                            let subWin=window.open(edit_url, '_blank');

                        }}}

            } // if(svg)

        } // if(event.shiftKey)

    } // into_folder()



    function check_js(link){
        let filename=link.textContent;
        if(filename.includes('user.js') || filename.includes('index.html')){
            return false; }
        else{
            return true; }}

} // to_edit()



function input_filename(){
    folder_name=localStorage.getItem("GOV_name");
    if(folder_name===null || folder_name===''){
        return; }

    set_ver=localStorage.getItem("GOV_ver");
    if(set_ver===null){
        return; }
    let ver_text; // 連番表記
    if(set_ver==-1){
        ver_text=''; } // -1の時は連番無し
    else{
        ver_text=set_ver.toString(); }

    let file_name=location.href.split('/edit/main/')[1]?.split('?')[0];
    if(!file_name){
        return; }

    let new_name=folder_name + ver_text +'/'+ file_name;

    let input_name=document.querySelector('input[aria-label="File name"]');
    if(input_name && new_name){
        // JavaScriptのセッターの標準プロパティを取得
        let valueSetter=
            Object.getOwnPropertyDescriptor(window.HTMLInputElement.prototype, "value").set;
        // Reactの内部状態をバイパスして値を強制的に書き込む
        valueSetter.call(input_name, new_name);
        //「ユーザーが入力した」というイベントを発生
        let event=new Event('input', { bubbles: true });
        input_name.dispatchEvent(event); }



    window.addEventListener('pagehide', ()=>{ // 編集画面を閉じるとルート画面をリロードする
        if(window.opener && !window.opener.closed){ // 親ウィンドウが閉じられていない場合
            window.opener.location.reload(); }});

} // input_filename()
