// ==UserScript==
// @name        AmbTV OnAir
// @namespace        http://tampermonkey.net/
// @version        4.1
// @description        AbemaTV ユーティリティ
// @author        AbemaTV User
// @match        https://abema.tv/*
// @icon        https://www.google.com/s2/favicons?sz=64&domain=abema.tv
// @noframes
// @grant        none
// @updateURL        https://github.com/personwritep/AmbTV_OnAir/raw/main/AmbTV_OnAir.user.js
// @downloadURL        https://github.com/personwritep/AmbTV_OnAir/raw/main/AmbTV_OnAir.user.js
// ==/UserScript==


let oa_mute;
let oa_vol;
let oa_size;
let oa_opac;
let oa_channel;
let muted=1; // ミュート状態のフラグ 0:ミュート 1:通常


let target=document.querySelector('head > title');
let monitor0=new MutationObserver(tv_player_env);
monitor0.observe(target, { childList: true });

tv_player_env();

function tv_player_env(){
    let retry=0;
    let interval=setInterval(wait_target, 20);
    function wait_target(){
        retry++;
        if(retry>100){ // リトライ制限 100回 2secまで
            clearInterval(interval); }
        let TP=document.querySelector('.com-tv-TVScreen__player');
        if(TP){
            clearInterval(interval);
            player_vol(TP); }}


    history_content();

} // tv_player_env()



function player_vol(TP){
    let monitor1=new MutationObserver(con_vol);
    monitor1.observe( TP, { childList: true });

    con_vol();

    function con_vol(){ // ABEMAロゴによるミュート
        let LF=document.querySelector('.com-tv-LinearFooter__feed-super');
        if(TP.querySelector('.com-tv-TVScreen__eyecatch')){
            if(LF.textContent){
                mute_act(1); }}
        else{
            if(!LF.textContent){
                mute_act(0); }}

    } // con_vol()



    let LF=document.querySelector('.com-tv-LinearFooter__feed-super');
    let monitor2=new MutationObserver(con_vol2);
    monitor2.observe( LF, { childList: true });

    con_vol2();

    function con_vol2(){ // 動画タイトルによるミュート
        if(LF.textContent){
            mute_act(1); }
        else{
            setTimeout(()=>{
                ad_check();
            }, 200); }}


    function ad_check(){
        let cvs=
            '<canvas id="cvs" style="position: fixed; z-index: -1; visibility: hidden;">'+
            '</canvas>';
        if(!document.querySelector('#cvs')){
            document.body.insertAdjacentHTML('beforeend', cvs); }
        let canvas=document.querySelector('#cvs');


        let retry_s=0;
        let interval_s=setInterval(cv_check, 1000);
        function cv_check(){
            retry_s++
            if(retry_s>15){ // リトライ制限 15sec
                clearInterval(interval_s); }
            capture(canvas);

            function capture(canvas){
                let video=
                    document.querySelector('.com-a-Video__video video[src]');
                if(video){
                    canvas.width=1;
                    canvas.height=1;
                    canvas.getContext('2d').drawImage(video, 0, 0, canvas.width, canvas.height);
                    if(canvas.getContext('2d')){
                        let imageData=canvas.getContext('2d').getImageData(0, 0, 1, 1);
                        let data=imageData.data;

                        if(data[0]+data[1]+data[2]!=0){ // ADの場合
                            mute_act(0);
                            retry_s=16; }}}} // capture()

        } // cv_check()

    } // ad_check()



    setTimeout(()=>{
        let LCLI=document.querySelector('.com-tv-LinearChannelListItem--active a');
        if(LCLI){
            let monitor3=new MutationObserver(con_vol3);
            monitor3.observe( LCLI, { attributes: true });

            con_vol3();

            function con_vol3(){
                mute_act(1);
                con_vol2(); }}
    }, 200 );



    setTimeout(()=>{
        let side=document.querySelector('.com-tv-FeedSidePanel__close-button');
        if(side){
            side.click(); }
    }, 600);

    setTimeout(()=>{
        let HM=document.querySelector('.com-m-HeaderMenu');
        let SNc=document.querySelector('.c-application-SideNavigation--collapsed');
        if(HM && !SNc){
            HM.click(); }
    }, 700);



    check_cookie();
    cm_setting();
    channel_setting();
    ex_view();

    setTimeout(()=>{
        vol_set();
    }, 600);

} // player_vol(TP)



function mute_act(n){ // 0: ミュート　1: 通常 🟨
    oa_mute=get_cookie('oa_mute');

    if(n==0){
        if(oa_mute==0){
            muted=0;
            sound(0);
            view(0); }}
    else{
        muted=1;
        sound(1);
        view(1); }


    function sound(n){ // 0: ミュート  1: 通常 🟨
        oa_vol=get_cookie('oa_vol');
        let vol_val=[0, 0.1, 0.2, 0.4, 0.6, 1]; // 音量のデフォルト「0」
        let mvol=vol_val[oa_vol];

        let video=document.querySelector('.com-a-Video__video video[src]');
        if(video){
            let reference=localStorage.getItem('AmbTVOA_V'); // 🟨
            if(n==0){
                slide_down(reference); }
            else{
                slide_up(reference); }}


        function slide_down(reference){
            let retry=0;
            let vol;
            let interval=setInterval(slide, 50);
            function slide(){
                retry++;
                if(retry>9){
                    clearInterval(interval); }
                vol=mvol*retry+10-retry;
                video.volume=reference*vol/10; }} // 🟨


        function slide_up(reference){
            let retry=0;
            let vol;
            let interval=setInterval(slide, 50);
            function slide(){
                retry++;
                if(retry>9){
                    clearInterval(interval); }
                vol=mvol*(10-retry)+retry;
                video.volume=reference*vol/10; }} // 🟨

    } // sound()


    function view(n){ // 0: ミュート  1: 通常
        oa_opac=get_cookie('oa_opac');
        let opac_val=[0.5, 0, 1]; // 明度のデフォルト「0.5」
        oa_size=get_cookie('oa_size');
        let size_val=[0.5, 1]; // サイズのデフォルト「0.5」

        let TVS=document.querySelector('.com-tv-TVScreen__player');
        if(TVS){
            if(n==0){
                TVS.style.transition='opacity .5s, transform .5s';
                TVS.style.opacity=opac_val[oa_opac];
                TVS.style.transform='scale('+ size_val[oa_size] +')'; }
            else{
                TVS.style.transition='';
                TVS.style.opacity='';
                TVS.style.transform=''; }}}

} // mute_act()



function get_cookie(name){
    let cookie_req=document.cookie.split('; ').find(row=>row.startsWith(name));
    if(cookie_req){
        if(cookie_req.split('=')[1]==null){
            return 0; }
        else{
            return cookie_req.split('=')[1]; }}
    if(!cookie_req){
        return 0; }}



function check_cookie(){
    oa_mute=get_cookie('oa_mute');
    document.cookie='oa_mute='+oa_mute+'; path=/; Max-Age=2592000';

    oa_vol=get_cookie('oa_vol');
    document.cookie='oa_vol='+oa_vol+'; path=/; Max-Age=2592000';

    oa_size=get_cookie('oa_size');
    document.cookie='oa_size='+oa_size+'; path=/; Max-Age=2592000';

    oa_opac=get_cookie('oa_opac');
    document.cookie='oa_opac='+oa_opac+'; path=/; Max-Age=2592000';

} // check_cookie()



function cm_setting(){
    let protect=0; //「ブラウザ表示」のボタンによる手動ミュート適用防止

    let TVS=document.querySelector('.com-tv-TVScreen__player');
    if(TVS){
        let monitor4=new MutationObserver(safe);
        monitor4.observe(TVS, { childList: true });

        function safe(){
            let buttons=TVS.querySelectorAll('.com-tv-TVController button');
            for(let k=0; k<buttons.length; k++){
                buttons[k].addEventListener('mouseenter', function(){
                    sp(1); });
                buttons[k].addEventListener('mouseleave', function(){
                    sp(0); }); }
            function sp(n){
                protect=n; }}


        TVS.onclick=function(event){
            if(protect==0){
                if(muted==1){
                    mute_act(0); }
                else{
                    mute_act(1); }}}

    } // if(TVS)



    ti_view();

    window.addEventListener('resize', function(){
        setTimeout(()=>{
            ti_view();
        }, 100); });

    function ti_view(){
        let tooltip=document.querySelectorAll('.com-tv-TVController__fullscreen .com-a-Tooltip');
        for(let k=0; k<tooltip.length; k++){
            if(not_fullscreen()){
                tooltip[k].textContent='フルスクリーン(F11)'; }
            else{
                tooltip[k].textContent='ブラウザ表示(F11)'; }}

        let icon_svg=document.querySelectorAll('.com-tv-TVController__fullscreen-icon svg');
        for(let k=0; k<icon_svg.length; k++){
            if(not_fullscreen()){
                icon_svg[k].innerHTML=
                    '<use xlink:href="/assets/images/icons/player/fullscreen.svg?'+
                    'v=c903638372bf698151eb#svg-body"></use>'; }
            else{
                icon_svg[k].innerHTML=
                    '<use xlink:href="/assets/images/icons/player/fullscreen_exit.svg?'+
                    'v=765f7ba3308158737dbc#svg-body"></use>'; }}

    } // ti_view()



    let NOAC=document.querySelector('.c-tv-NowOnAirContainer');
    if(NOAC){
        NOAC.oncontextmenu=function(event){
            let clear_style=document.querySelector('.oa_clear_style');
            let disp_style=document.querySelector('.oa_disp_style');
            if(!event.ctrlKey || !event.shiftKey){
                if(clear_style.disabled==true){
                    disp_style.disabled=true;
                    clear_style.disabled=false; }
                else{
                    disp_style.disabled=false;
                    clear_style.disabled=true; }}}

        document.addEventListener('keydown', function(event){
            if(event.keyCode=='27'){
                let clear_style=document.querySelector('.oa_clear_style');
                if(clear_style.disabled==false){
                    clear_style.disabled=true; }}});

    } // if(NOAC && clear_style)

} // cm_setting()



function cm_pannel(){
    let help_url="https://ameblo.jp/personwritep/entry-12856628930.html";

    let help_SVG=
        '<svg class="oa_help" width="20"  height="20" viewBox="0 0 150 150">'+
        '<path  fill="#fff" d="M66 13C56 15 47 18 39 24C-12 60 18 146 82 137C92 '+
        '135 102 131 110 126C162 90 128 4 66 13M68 25C131 17 145 117 81 '+
        '125C16 133 3 34 68 25M69 40C61 41 39 58 58 61C66 63 73 47 82 57C84 '+
        '60 83 62 81 65C77 70 52 90 76 89C82 89 82 84 86 81C92 76 98 74 100 66'+
        'C105 48 84 37 69 40M70 94C58 99 66 118 78 112C90 107 82 89 70 94z">'+
        '</path></svg>';

    let panel=
        '<div id="amboa">'+
        '<div id="oa_head">　　　CMのミュート設定　　　　'+
        '<a href="'+ help_url +'" rel="noopener noreferrer" target="_blank">'+
        help_SVG +'</a>　'+
        '<input type="button" id="oa_close" value="×"></div>'+
        '<div class="oa_p">ミュート機能の有効 / 無効</div>'+
        '<div>　ミュート機能： '+
        '<input name="mute" type="radio" id="m0">有効　'+
        '<input name="mute" type="radio" id="m1">無効'+
        '</div>'+
        '<div class="oa_p">ミュート時の音量の設定</div>'+
        '<div>　音量： '+
        '<input name="volume" type="radio" id="v0" class="oa_cont">0　'+
        '<input name="volume" type="radio" id="v1" class="oa_cont">1　'+
        '<input name="volume" type="radio" id="v2" class="oa_cont">2　'+
        '<input name="volume" type="radio" id="v3" class="oa_cont">4　'+
        '<input name="volume" type="radio" id="v4" class="oa_cont">6　'+
        '<input name="volume" type="radio" id="v5" class="oa_cont">10'+
        '</div>'+
        '<div class="oa_p">ミュート時の画面の設定</div>'+
        '<div>　画面サイズ： '+
        '<input name="size" type="radio" id="s0" class="oa_cont">縮小　'+
        '<input name="size" type="radio" id="s1" class="oa_cont">通常'+
        '</div>'+
        '<div>　画面の明度： '+
        '<input name="opacity" type="radio" id="o1" class="oa_cont">0%　'+
        '<input name="opacity" type="radio" id="o0" class="oa_cont">50%　'+
        '<input name="opacity" type="radio" id="o2" class="oa_cont">100%'+
        '</div>'+

        '<style>#amboa { position: fixed; top: 60px; left: calc(50% - 190px); '+
        'font: 16px/24px Meiryo; color: #000; padding: 16px 16px 8px; width: 380px; '+
        'border: 1px solid #aaa; border-radius: 6px; background: #fff; z-index: 100; } '+
        '#oa_head { margin: 0 0 15px; padding: 5px 15px 3px; '+
        'font-weight: bold; color: #fff; background: #2196f3; text-align: center; } '+
        '.oa_help { vertical-align: -5px; } '+
        '#oa_close { padding: 0 2px; height: 20px; line-height: 16px; } '+
        '.oa_p { padding: 2px 8px 0; margin: 10px 0 6px; border: 1px solid #aaa; '+
        'line-height: 22px; } '+
        'input[type="radio"]{ margin: 0 .2em; }'+
        '</style>'+
        '</div>';
    if(!document.querySelector('#amboa')){
        document.body.insertAdjacentHTML('beforeend', panel); }

    live_mute();
    set_radio();

    function set_radio(){
        oa_mute=get_cookie('oa_mute');
        for(let k=0; k<2; k++){
            let m=document.querySelector('#m'+k);
            if(oa_mute==k){
                m.checked=true;
                mute(k);
                document.cookie='oa_mute='+k+'; path=/; Max-Age=2592000'; }

            m.onchange=function(){
                mute(k);
                document.cookie='oa_mute='+k+'; path=/; Max-Age=2592000';
                live_mute(); }}


        oa_vol=get_cookie('oa_vol'); // 🟨
        for(let k=0; k<6; k++){
            let v=document.querySelector('#v'+k);
            if(oa_vol==k){
                v.checked=true;
                document.cookie='oa_vol='+k+'; path=/; Max-Age=2592000'; }

            v.onchange=function(){
                document.cookie='oa_vol='+k+'; path=/; Max-Age=2592000';
                live_mute(); }}


        oa_size=get_cookie('oa_size');
        for(let k=0; k<2; k++){
            let s=document.querySelector('#s'+k);
            if(oa_size==k){
                s.checked=true;
                document.cookie='oa_size='+k+'; path=/; Max-Age=2592000'; }

            s.onchange=function(){
                document.cookie='oa_size='+k+'; path=/; Max-Age=2592000';
                live_mute(); }}


        oa_opac=get_cookie('oa_opac');
        for(let k=0; k<3; k++){
            let o=document.querySelector('#o'+k);
            if(oa_opac==k){
                o.checked=true;
                document.cookie='oa_opac='+k+'; path=/; Max-Age=2592000'; }

            o.onchange=function(){
                document.cookie='oa_opac='+k+'; path=/; Max-Age=2592000';
                live_mute(); }}


        function mute(n){
            let oa_cont=document.querySelectorAll('.oa_cont');
            for(let k=0; k<oa_cont.length; k++){
                if(n==0){
                    oa_cont[k].disabled=false; }
                else{
                    oa_cont[k].disabled=true; }}}

    } // set_radio()


    let amboa=document.querySelector('#amboa');
    let oa_close=document.querySelector('#oa_close');
    if(amboa && oa_close){
        oa_close.onclick=function(event){
            event.preventDefault();
            amboa.remove(); }}


    function live_mute(){
        let LF=document.querySelector('.com-tv-LinearFooter__feed-super');
        if(!LF.textContent){
            setTimeout(()=>{
                oa_mute=get_cookie('oa_mute');
                mute_act(oa_mute);
            }, 200); }}

} // cm_pannel()



function channel_setting(){
    let header_right=document.querySelector('.com-application-Header__right');
    if(header_right){
        let sw=
            '<div class="cms_sw">CM Mute</div>'+
            '<div class="cha_sw">Channel <span>▢</span></div>'+
            '<style>'+
            '.com-application-Header__right { display: flex; flex-basis: 440px !important; } '+
            '.cms_sw, .cha_sw { font: 14px Meiryo; align-self: center; cursor: pointer; '+
            'padding: 12px 6px 0; height: 46px; white-space: nowrap; color: #fff; '+
            'border: 1px solid #333; border-radius: 4px; background: #212121; } '+
            '.cms_sw { margin-right: 20px; display: none; } '+
            '.cha_sw { margin-right: 30px; display: none; } '+
            '.cha_sw span { display: inline-block; } '+
            '.cms_sw:hover, .cha_sw:hover { background: #373737; } '+
            '</style>'+

            '<style class="header_style">'+
            '.com-application-Header { background: #00000040; } '+
            '.cms_sw, .cha_sw { display: block; } '+
            '</style>'+

            '<style>'+
            '.com-application-SideNavigation, '+
            '.com-application-SideNavigation__wrapper { background: none; } '+
            '.com-application-SideNavItemList { height: 100%; background: #00000040; } '+
            '.com-tv-TVScreen__player { background-color: #000; } '+
            '.com-tv-LinearFooter { height: 124px; background: none; } '+
            '.com-tv-LinearFooter__bottom-block { background: #00000040; } '+
            '.com-tv-TVController button { outline: none; } '+
            '.com-a-Slider__highlighter { background-color: #2196f3; } '+

            '.com-tv-LinearChannelList { scrollbar-width: none; margin-right: 8px; } '+
            '.com-tv-LinearChannelList__inner { flex-wrap: wrap; flex-direction: row; '+
            'justify-content: flex-start; padding: 6px 0 0 4px; background: #b0bec5; } '+
            '.com-tv-LinearChannelListItem { padding: 0 2px; line-height: 0; } '+
            '.com-tv-LinearChannelListItem__outer { border-radius: 5px; } '+
            '.com-tv-LinearChannelListItem__inner { background-color: #000; padding: 1px; } '+
            '.com-tv-LinearChannelListItem--active .com-tv-LinearChannelListItem__inner { '+
            'background: #fff; } '+
            '.com-tv-LinearChannelListItem__thumbnail { '+
            'height: 57.5px !important; width: 103px !important; } '+
            '.com-tv-LinearChannelListItem--active .com-tv-LinearChannelListItem__title, '+
            '.com-tv-LinearChannelListItem--active '+
            '.com-tv-LinearChannelListItem__broadcasting-date { color: #000; } '+

            '.c-application-DesktopAppContainer__content { min-width: 436px; } '+
            '.com-tv-LinearChannelList--shrunk { width: 288px !important; } '+
            '@media screen and (min-width: 500px){ '+
            '.com-tv-LinearChannelList { width: 225px; }} '+
            '.com-tv-LinearChannelListItem--active '+
            '.com-tv-LinearChannelListItem__logo--shrunk { '+
            'filter: invert(1); height: 24px; } '+
            '</style>'+

            '<style class="cha_style">'+
            '.com-tv-LinearChannelList:before { height: 90px !important; } '+
            '.com-tv-LinearChannelList:after { height: 120px !important; } '+
            '@media screen and (min-width: 640px){ '+
            '.com-tv-LinearChannelList { width: 442px; }} '+
            '@media screen and (min-width: 860px){ '+
            '.com-tv-LinearChannelList { width: 659px; }} '+
            '@media screen and (min-width: 1080px){ '+
            '.com-tv-LinearChannelList { width: 876px; }} '+
            '</style>'+

            '<style class="oa_clear_style">'+
            '.c-common-HeaderContainer-header { opacity: 0; visibility: hidden; } '+
            '.com-application-SideNavigation { display: none; } '+
            '.c-tv-NowOnAirContainer__remote-controller { display: none; } '+
            '.com-tv-TVScreen__footer-container { '+
            'transform: translateY(0); visibility: hidden; transition: padding-left 0s; } '+
            'button:enabled { cursor: none; } '+ // カーソル非表示
            '</style>'+

            '<style class="oa_disp_style">'+
            '.c-common-HeaderContainer-header { opacity: 1; visibility: visible; } '+
            '.com-application-SideNavigation { display: flex; opacity: 1; visibility: visible; } '+
            '.c-tv-NowOnAirContainer__remote-controller { display: block; } '+
            '.com-tv-TVScreen__footer-container { transition: padding-left 0s; '+
            'transform: translateY(0); visibility: visible; padding-left: 64px; } '+
            '</style>'+

            '<style class="ex_view_style">'+
            '.com-tv-TVScreen__player { height: 100vh !important; '+
            'width: 132%; margin: 0 -16%; }'+
            '.com-tv-TVController__fullscreen-button { color: red; } '+
            '</style>'+

            '<style class="vol_set_style">'+
            '.com-playback-Volume .com-playback-Volume__slider-container { '+
            'opacity: 1; visibility: visible; } '+
            '</style>';

        if(!header_right.querySelector('.cms_sw')){
            header_right.insertAdjacentHTML('afterbegin', sw); }

        let clear_style=document.querySelector('.oa_clear_style');
        if(clear_style){
            clear_style.disabled=true; }

        let disp_style=document.querySelector('.oa_disp_style');
        if(disp_style){
            disp_style.disabled=true; }

        let ex_view_style=document.querySelector('.ex_view_style');
        if(ex_view_style){
            ex_view_style.disabled=true; }

        let vol_set_style=document.querySelector('.vol_set_style');
        if(vol_set_style){
            vol_set_style.disabled=true; }

        let cha_style=document.querySelector('.cha_style');
        let cha_sw=document.querySelector('.cha_sw');
        if(cha_style && cha_sw){
            oa_channel=get_cookie('oa_channel');
            if(oa_channel!='1'){
                oa_channel='0';
                document.cookie='oa_channel=0; path=/; Max-Age=2592000';
                sw_view(0);
                cha_style.disabled=true; }
            else{
                oa_channel='1';
                document.cookie='oa_channel=1; path=/; Max-Age=2592000';
                sw_view(1);
                cha_style.disabled=false; }

            cha_sw.onclick=function(){
                if(oa_channel=='0'){
                    oa_channel='1'
                    document.cookie='oa_channel=1; path=/; Max-Age=2592000';
                    sw_view(1);
                    cha_style.disabled=false; }
                else{
                    oa_channel='0';
                    document.cookie='oa_channel=0; path=/; Max-Age=2592000';
                    sw_view(0);
                    cha_style.disabled=true; }
                cha_check(); }

            function sw_view(n){
                let swsp=cha_sw.querySelector('span');
                if(swsp){
                    if(n==0){
                        swsp.style.transform='scaleX(0.5)'; }
                    else{
                        swsp.style.transform='scaleX(1)'; }}}

            function cha_check(){
                let swicher=document.querySelector('.com-tv-LinearChannelSwitcher button');
                if(swicher){
                    if(document.createEvent){
                        let evt=new Event('mouseover', { bubbles: true, cancelable: false });
                        swicher.dispatchEvent(evt); }}}

        } // if(cha_style && cha_sw)



        let cms_sw=document.querySelector('.cms_sw');
        if(cms_sw){
            cms_sw.onclick=function(){
                let amboa=document.querySelector('#amboa');
                if(!amboa){
                    cm_pannel(); }
                else{
                    amboa.remove(); }}}}

} // channel_setting()



function ex_view(){
    let ex_view_style=document.querySelector('.ex_view_style');
    let fs_b=document.querySelector('.com-tv-TVController__fullscreen-button');
    if(ex_view_style && fs_b){
        fs_b.onclick=function(event){
            event.preventDefault();
            event.stopImmediatePropagation();
            if(event.ctrlKey){
                if(ex_view_style.disabled==true){
                    ex_view_style.disabled=false; }
                else{
                    ex_view_style.disabled=true; }}
            else{
                full(); }}}


    function full(){
        if(not_fullscreen()){
            if(document.documentElement.webkitRequestFullscreen){
                document.documentElement.webkitRequestFullscreen(); }
            else if(document.documentElement.requestFullscreen){
                document.documentElement.requestFullscreen(); }}
        else{
            document.exitFullscreen(); }}

} // ex_view()



function vol_set(){
    let video=document.querySelector('.com-a-Video__video video[src]');
    let slider=document.querySelector('.com-playback-Volume__slider-container');
    if(video && slider){
        video.addEventListener('volumechange', ()=>{
            let opa=getComputedStyle(slider).opacity;
            if(opa!=0 && muted==1){ // スライダーが表示されている時のみ音量をストレージ記録 🟨
                let setVolume=Math.round(video.volume*10)/10
                localStorage.setItem('AmbTVOA_V', setVolume); }}); }



    document.addEventListener('keydown', function(event){
        if(event.shiftKey){
            slider_disp(1);

            if(event.keyCode=='40'){ //「⇩」キー Vol Down　🟨
                event.preventDefault();
                event.stopImmediatePropagation();
                vol_con(0); }

            if(event.keyCode=='38'){ //「⇧」キー Vol Up　🟨
                event.preventDefault();
                event.stopImmediatePropagation();
                vol_con(1); }

        }}, true ); // true必須


    document.addEventListener('keyup', function(event){
        if(!event.shiftKey){
            slider_disp(0);
        }}, true);


    function vol_con(n){
        let video=document.querySelector('.com-a-Video__video-element'); // 🟨
        if(video){
            if(n==0){
                if(video.volume>=0.1){
                    video.volume -=0.1 }}
            if(n==1){
                if(video.volume<=0.9){
                    video.volume +=0.1 }}}}


    function slider_disp(n){
        let vol_set_style=document.querySelector('.vol_set_style');
        if(vol_set_style){
            if(n==0){
                vol_set_style.disabled=true; }
            else{
                vol_set_style.disabled=false; }}}

} // vol_set()



function not_fullscreen(){
    if(window.screen.height-(window.innerHeight)*(window.devicePixelRatio)<50 ){
        return false; }
    else{
        return true; }}



function history_content(){

    if(location.pathname.startsWith('/now-on-air/')){
        header_view(1);
        get_title(); }
    else{
        header_view(0);
        setTimeout(()=>{
            get_title_top();
            set_last();
        }, 600); }


    function get_title(){
        let LCL=document.querySelectorAll('.com-tv-LinearChannelListItem');
        if(LCL.length>0){
            for(let k=0; k<LCL.length; k++){
                LCL[k].onclick=()=>{
                    let lasttitle=set_histort(LCL[k]);
                    sessionStorage.setItem('ATV_OA', lasttitle); }

                function set_histort(link){
                    let title=link.querySelector('.com-tv-LinearChannelListItem__title');
                    if(title && title.textContent){
                        return title.textContent; }}}}}


    function get_title_top(){
        let SGCC=document.querySelectorAll('.com-pages-home-ScheduleGroupContentCardItem');
        for(let k=0; k<SGCC.length; k++){
            SGCC[k].onclick=()=>{
                let container=SGCC[k].querySelector('.com-a-CollapsedText__container');
                if(container && container.textContent){
                    sessionStorage.setItem('ATV_OA', container.textContent); }}}}


    function set_last(){
        let lasttitle=sessionStorage.getItem('ATV_OA');
        let SGCC=document.querySelectorAll('.com-pages-home-ScheduleGroupContentCardItem');
        for(let k=0; k<SGCC.length; k++){
            let container=SGCC[k].querySelector('.com-a-CollapsedText__container');
            if(container){
                if(container.textContent==lasttitle){
                    SGCC[k].click();
                    setTimeout(()=>{
                        scroll_center(SGCC[k]);
                    }, 200); }}}


        function scroll_center(target){
            let SGCCB=document.querySelector(
                '.com-pages-home-ScheduleGroupContentCarouselBase__slide-list');
            if(SGCCB){
                let half_width=SGCCB.clientWidth/2
                let scroll_w=target.offsetLeft - SGCCB.offsetLeft - half_width;
                SGCCB.scrollTo(scroll_w, 0); }}

    } // set_last()


    function header_view(n){
        let header_style=document.querySelector('.header_style');
        if(header_style){
            if(n==0){
                header_style.disabled=true; }
            else{
                header_style.disabled=false; }}}

} // history_content()
