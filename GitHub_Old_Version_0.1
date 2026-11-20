// ==UserScript==
// @name        GitHub Old_Version 🔵
// @namespace        http://tampermonkey.net/
// @version        0.1
// @description        Old_Versionフォルダーに整理処理を補助する　「Shift+右Click」
// @author        personwritep
// @match        https://github.com/*
// @icon        https://www.google.com/s2/favicons?sz=64&domain=github.com
// @grant        none
// @updateURL        https://github.com/personwritep/GitHub_Old_Version/raw/main/GitHub_Old_Version.user.js
// @downloadURL        https://github.com/personwritep/GitHub_Old_Version/raw/main/GitHub_Old_Version.user.js
// ==/UserScript==

let set_ver; // セッション中のフォルダー番号

let lastUrl=location.href; // 現在のURLを保存

let target=document.querySelector('head');
let monitor=new MutationObserver(()=>{
    if(location.href !==lastUrl){
        lastUrl=location.href; // 新しいURLに更新
        main(); }});

monitor.observe(target, { childList: true });

main();

function main(){
    let q=window.location.search;
    if(q.includes('Old') && !q.includes('search')){ // クエリ文字列「Old」で起動
        setTimeout(()=>{
            input_filename();
        }, 800); }
    else{
        set_version();
        to_edit(); }}




function input_filename(){
    let ver_num=localStorage.getItem("GOV_ver");
    if(ver_num===null){
        return; }

    let file_name=location.href.split('/edit/main/')[1]?.split('?')[0];
    if(!file_name){
        return; }

    let new_name='Old_Version_'+ ver_num +'/'+ file_name;

    let input_name=document.querySelector('input[aria-label="File name"]');
    if(input_name && new_name){
            // JavaScriptのセッターの標準プロパティを取得
            let valueSetter=
                Object.getOwnPropertyDescriptor(window.HTMLInputElement.prototype, "value").set;
            // Reactの内部状態をバイパスして値を強制的に書き込む
            valueSetter.call(input_name, new_name);
            //「ユーザーが入力した」というイベントを発生
            let event=new Event('input', { bubbles: true });
            input_name.dispatchEvent(event);
    }

} // input_filename()




function set_version(){
    let panel=
        '<div id="version_panel">'+
        'Ver No: <input class="ver_num" type="number" min="1" step="1">'+
        '<style>'+
        '#version_panel { position: fixed; top: 17px; left: 410px; z-index: 100; '+
        'padding: 3px 6px; border-radius: 6px; color: #fff; background: red; '+
        'font: normal 16px/22px Meiryo; } '+
        '.ver_num { width: 48px; padding: 2px 2px 0px 4px; text-align: center; '+
        'border: 1px solid #ccc; border-radius: 3px; outline: none !important; } '+
        'input[type=number].ver_num::-webkit-inner-spin-button { '+
        'height: 16px; margin-top: 2px; appearance: auto; } '+
        '</style></div>';

    if(!document.querySelector('#version_panel')){
        document.body.insertAdjacentHTML('beforeend', panel); }

    set_ver=localStorage.getItem("GOV_ver");
    if(set_ver===null || set_ver<1){
        set_ver=1; }
    localStorage.setItem("GOV_ver", set_ver);

    let ver_num=document.querySelector('#version_panel .ver_num');
    if(ver_num){
        ver_num.value=set_ver; }

    ver_num.oninput=()=>{
        localStorage.setItem("GOV_ver", ver_num.value); }

} // set_version()




function to_edit(){

    document.addEventListener('contextmenu', (event)=>{
        let row=event.target.closest('.react-directory-row');
        if(!row){
            return; }
        event.preventDefault();
        event.stopPropagation();
        in_old_version(row, event);
    }, true);


    function in_old_version(row, event){
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

                            edit_url=root +'/edit/main/'+ file_name +'?Old'; // クエリ「Old」を設定
                            let subWin=window.open(edit_url, '_blank');

                            if(subWin){
                                let timer=setInterval(function(){
                                    if(subWin.closed){
                                        clearInterval(timer); // 監視を終了
                                        location.reload(); } // 元画面をリロード
                                }, 1000); }

                        }}}} // if(svg)

        } // if(event.shiftKey)

    } // in_old_version()



    function check_js(link){
        let filename=link.textContent;
        if(filename.includes('user.js') || filename.includes('index.html')){
            return false; }
        else{
            return true; }}

} // to_edit()
