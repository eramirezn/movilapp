<!DOCTYPE html>
<!--
    Licensed to the Apache Software Foundation (ASF) under one
    or more contributor license agreements.  See the NOTICE file
    distributed with this work for additional information
    regarding copyright ownership.  The ASF licenses this file
    to you under the Apache License, Version 2.0 (the
    "License"); you may not use this file except in compliance
    with the License.  You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing,
    software distributed under the License is distributed on an
    "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
     KIND, either express or implied.  See the License for the
    specific language governing permissions and limitations
    under the License.
-->
<html>
    <head>
        <meta charset="utf-8" />
        <meta name="format-detection" content="telephone=no" />
        <!-- WARNING: for iOS 7, remove the width=device-width and height=device-height attributes. See https://issues.apache.org/jira/browse/CB-4323 -->
        <meta name="viewport" content="user-scalable=no, initial-scale=1, maximum-scale=1, minimum-scale=1, width=device-width, height=device-height, target-densitydpi=device-dpi" />
        <link rel="stylesheet" type="text/css" href="css/index.css" />
        <link rel="stylesheet" type="text/css" href="js/jQueryMobile/jquery.mobile-1.4.2.min.css"/>
        <link rel="stylesheet" type="text/css" href="js/jQueryMobile/jquery.mobile.theme-1.4.2.min.css"/>
        <link rel="stylesheet" type="text/css" href="css/estilos.css">
        <script type="text/javascript" src="js/jquery-1.11.1.min.js"></script>
        <script type="text/javascript" src="js/jQueryMobile/jquery.mobile-1.4.2.min.js"></script>
        <script type="text/javascript" src="js/funcionesGlobales.js"></script>
        <script type="text/javascript" src="js/funcionesGenerales.js"></script>
        <title>Operador Olva App</title>
    </head>
    <body>
        <div class="app">
            <h1>Apache Cordova</h1>
            <div id="deviceready" class="blink">
                <p class="event listening">Connecting to Device</p>
                <p class="event received">Device is Ready</p>
            </div>
        </div>
<div data-role="page" id="pageLogin">

    <div data-role="header" data-theme="b">
        <h1>Autenticacion</h1>
    </div><!-- /header -->

    <div role="main" class="ui-content">
        <h4>Iniciar Sesion:</h4>
        <form>
            <label type="text" id="lbl_msgLogin" class="alertHid"></label>
            <input type="text" placeholder="Username" id="txt_username">
            <input type="password" placeholder="Password" id="txt_password">
            <input type="button" data-theme="a" value="Log In" data-icon="home" id="btnLogin">  
        </form>
    </div><!-- /content -->
</div><!-- /page -->
<div data-role="page" id="pageMenuPrincipal" data-theme="a">
    <div data-role="header" data-theme="b">
         <label type="text" id="lbl_operador"></label>
         <!--<input type="button" id="btn_logOff" value="Log Off">  -->
        <a href="#" data-theme="b" data-direction="reverse" id="btn_logOut" data-icon="back">Log Out</a> 
        <h1>Menu Principal</h1>
    </div><!-- /header -->
    <div role="main" class="ui-content">
         <input type="button" id="btn_opcionDist" data-icon="grid" data-theme="a" value="Distribucion">  
         <input type="button" id="btn_opcionReco" data-icon="grid" data-theme="c" value="Recojos">  

    </div><!-- /content -->
</div><!-- /page -->
<!-- Start of second page -->
<div data-role="page" id="pageRecojosMain">
    <div data-role="header" data-theme="b">
        <!--<input type="button" id="btn_backToMenuMain" value="Atras">  -->
        <a href="#pageMenuPrincipal" data-theme="b" data-direction="reverse" data-icon="back">Atras</a> 
        <h1>Recojos Pendientes</h1>
    </div><!-- /header -->
    <div role="main" class="ui-content">
        <ul data-role="listview" data-inset="true"  id="recojosLista" class="ui-alt-icon"></ul>  


        <div class="ui-grid-a ui-bar ui-bar-e" data-theme="b">
            <div class="ui-block-a">
                <strong>Pendientes:</strong><strong id="total_pendientes"></strong>
            </div>
            <div class="ui-block-b">
                <!--<div><strong>Total:</strong></div>
                <div><strong id="total_recojos"></strong></div>-->
            </div>
        </div>
    </div>
</div>
<div data-role="page" id="pageRecojosDetalle">
    <div data-role="header" data-theme="b">
        <!--<input type="button"  id="btn_backToRecojosMain" value="Atras"> -->
        <a href="#pageRecojosMain" data-theme="b" data-direction="reverse" data-icon="back">Atras</a> 
        <h1>Detalle Recojo:</h1>
    </div><!-- /header -->
<div role="main" class="ui-content" id='contentRecDet'>
    

    <ul data-role="listview"  data-inset="true" id="detalleLista" class="ui-alt-icon">
        <li data-role="list-divider"><h4>Cliente:</h4></li>
        <li ><h4 id="nomcli_det"></h4></li>
        <li data-role="list-divider"><h4>Ruc:</h4></li>
        <li ><h4 id="ruc_det"></h4></li>
        <li data-role="list-divider"><h4>Contacto:</h4></li>
        <li ><h4 id="contacto_det"></h4></li>
        <li data-role="list-divider"><h4>Direccion:</h4></li>
        <li ><h4 id="dirrec_det"></h4></li>
        <li data-role="list-divider"><h4>Peso:</h4></li>
        <li ><h4 id="pesorec_det"></h4></li>
        <li data-role="list-divider"><h4>Glosa:</h4></li>
        <li ><div><h4 id="glosa_det"></h4></div></li>
        <!--<li data-role="list-divider"><h4>Estado Envio:</h4></li>
        <li ><h4 id="estado_envio_det"></h4></li>-->
        <li data-role="list-divider"><h4>Estado Recojo:</h4></li>
        <li ><h4 id="estado_recojo_det"></h4></li>
        <li data-role="list-divider"><h4>Hora Recojo:</h4></li>
        <li ><h4 id="_horarec_det"></h4></li>
        <li data-role="list-divider"><h4>Hora Recojo Final:</h4></li>
        <li ><h4 id="horafin_det"></h4></li>
    </ul>  
     <fieldset class="ui-grid-a">
                <div class="ui-block-a">
                    <input type="button" id="btn_confirmaRec" data-icon="check" data-theme="b" value="Confirmar">
                </div>
                <div class="ui-block-b">
                    <input type="button" id="btn_motivaRec" data-icon="delete" data-theme="b" value="Motivar"> 
                </div>
    </fieldset>
</div>
</div>
<div data-role="page" id="pageMotivar">
    <div data-role="header" data-theme="b">
        <!--<input type="button" id="btn_backToRecojDet" value="Atras"> -->
        <a href="#pageRecojosDetalle" data-theme="b" data-direction="reverse" data-icon="back">Atras</a> 
        <h1>Motivar recojo</h1>
    </div>
    <div role="main" class="ui-content">
        <fieldset data-role="controlgroup" id='motivos_opcion'></fieldset>      
        <div id="lbl_msgMotivar" class="alertHid"></div>            
        <input type="button" data-theme="b" data-icon="check" value="Aceptar" id='btn_aceptaMotivar'/>  
    </div>

</div>

<div data-role="page" id="pageIngresarOrden">
    <div data-role="header" data-theme="b">
        <!--<input type="button" id="btn_backToRecojDet" value="Atras"> -->
        <a href="#pageRecojosDetalle" data-theme="b" data-direction="reverse" data-icon="back">Atras</a> 
        <h1></h1>
    </div>
    <div role="main" class="ui-content">
        <fieldset   class="ui-grid-a">  
            <legend class="marcado">nro Documento:</legend>          
            <div id="div_txt_emiOrden" class="ui-block-a"><input type="text" placeholder="Emision" id="txt_emiOrden"></div>
            <div id="div_txt_numOrden" class="ui-block-b"><input type="text" placeholder="Numero" id="txt_numOrden"></div>
        </fieldset>  
        <label id="lbl_msgAddOrden" class="alertHid"></label>
        <fieldset   class="ui-grid-a">         
            <div class="ui-block-a center" id="cont_plus">
                <input class="botonera_orden" type="button" id="btn_addOrden" data-icon="plus" value="Agregar" data-theme="a">
            </div>
            <div class="ui-block-b center">
                <input class="botonera_orden" type="button" id="btn_delOrden" data-icon="minus"  value="Quitar" data-theme="a">
            </div>
        </fieldset> 

            <fieldset data-role="controlgroup" id="ordenesListChk">
              <legend class="marcado">O/S a crear para este recojo:</legend>
               <!--<input type="checkbox" name="checkbox-2" id="checkbox-2" class="custom" /><label for="checkbox-2">I agree</label>-->
            </fieldset>
        <!--<ul data-role="listview" data-inset="true"  id="ordenesLista" class="ui-alt-icon">
        </ul>-->
        <div id="div_btnAceptaConfirmar">
            <input type="button" data-theme="b" data-icon="check" value="Aceptar" id='btn_aceptaConfirmar'/>
        </div>
    </div>

</div>



        <script type="text/javascript" src="cordova.js"></script>
        <script type="text/javascript" src="js/index.js"></script>
        <script type="text/javascript">
            app.initialize();   
        </script>
    </body>
</html>


------------------------------------



 var obj_listado;
 var obj_motivos;
 var usuario_global;
 var password_global;
 var mask;
function linkrecojo(param){

  $.mobile.changePage( "#pageRecojosDetalle", { transition: "slide", changeHash: false });

  //alert(param)

  $("#nomcli_det").html('');
  $("#ruc_det").html('');
  $("#contacto_det").html('');
  //$("#numrec_det").html('');
  $("#dir_cliente").html('');
  $("#peso_envio").html('');
  $("#glosa").html('');
  $("#estado_envio").html('');
  $("#hora_recojo").html('');
  $("#hora_recojo_fin").html('');
  jQuery.each(obj_listado, function( i, obj ) {
   // alert(obj.nro_recojo + '-'+param );
    if(parseInt(obj.nro_recojo)==parseInt(param)){ 

      $("#pageRecojosDetalle div h1").html('');
      $("#pageRecojosDetalle div h1").html('Recojo Nro: '+parseInt(obj.nro_recojo));
      //$("#numrec_det").html(obj.nro_recojo);
      $("#nomcli_det").html(obj.nom_cli);
      $("#ruc_det").html(obj.ruc_dni);
      $("#contacto_det").html(obj.contacto);
      $("#dirrec_det").html(obj.dir_cliente);
      $("#pesorec_det").html(obj.peso_envio);
      $("#glosa_det").html(obj.glosa);
      //$("#estado_envio_det").html(obj.estado_envio);
      $("#estado_recojo_det").html(obj.estado_recojo);
      $("#_horarec_det").html(obj.hora_recojo);
      $("#horafin_det").html(obj.hora_recojo_fin);
    }
  });
}


 




$(document).ready(function(){
 
    $( "#btnLogin" ).click(function() {
      $("#lbl_msgLogin").html('');
      mask=$.mobile.loading( 'show', {
      text: 'Validando',
      textVisible: true,
      theme: 'b'
    });
    var username=$("#txt_username").val();
      var password=$("#txt_password").val();
      loginValidar(username, password);
    });
    $("#btn_opcionReco").click(function (){ 
        $.mobile.changePage( "#pageRecojosMain", { transition: "slide", changeHash: false });
    })
    $("#btn_logOut").click(function (){       
      obj_listado='';
      obj_motivos='';
      usuario_global='';
      password_global='';
      $.mobile.changePage( "#pageLogin", { transition: "slidedown", changeHash: false });
    })
    $("#btn_backToMenuMain").click(function (){     
        /*destruimos las credenciales*/
        $.mobile.changePage( "#pageMenuPrincipal", { transition: "slidedown", changeHash: false });
    })
    $("#btn_backToRecojosMain").click(function (){  
        $.mobile.changePage( "#pageRecojosMain", { transition: "slidedown", changeHash: false });

    })
    $("#btn_confirmaRec").click(function (){
    $.mobile.changePage( "#pageIngresarOrden", { transition: "slidedown", changeHash: false });
  })
  $("#btn_aceptaConfirmar").click(function (){      
    alert('cambia estado db')
    $.mobile.changePage( "#pageRecojosMain", { transition: "slidedown", changeHash: false });
    })
    $("#btn_motivaRec").click(function (){    
    $.mobile.changePage( "#pageMotivar", { transition: "slide", changeHash: false });    
      $("#lbl_msgMotivar").html(''); 
  })
  $("#btn_backToRecojDet").click(function (){   
    $.mobile.changePage( "#pageRecojosDetalle", { transition: "slidedown", changeHash: false });
  })
  $("#btn_aceptaMotivar").click(function (){   
        motivarRecojo();
  })  

  $("#btn_addOrden").click(function (){ 
       var msg="Ingrese la emision y el Numero";
       var txt_emision=trim($("#txt_emiOrden").val());
       var txt_numero=trim($("#txt_numOrden").val());

       $("#lbl_msgAddOrden").val('')

       if(txt_emision.length=='' || txt_numero.length==''){
         $("#lbl_msgAddOrden").html(msg)
         return false;
       }else{
         $("#ordenesListChk").append(
          '<label><input type="checkbox" class="chk_orden" name="checkbox-1" id="checkbox-1" />'+txt_emision+' - '+txt_numero+'</label>');
       }
       //$("#ordenesLista").listview('refresh');
       $("#txt_emiOrden").val('');
       $("#txt_numOrden").val('');
       $(".chk_orden").checkboxradio();
       $(".chk_orden").checkboxradio("refresh");
       $(".chk_orden").attr('checked',false).checkboxradio("refresh");
       $("#txt_emiOrden").focus();
  })


  $("#btn_delOrden").click(function (){
      $(".chk_orden").each(function(e){        
        if($(this).prop('checked')==true){    
          $(this).parent().remove();/*debemos eliminar al padre ya que el es el contenedor*/
        }        
      })
      $("#txt_emiOrden").focus();
  })

      function CargaLista( ){
    
     }






    function motivarRecojo(){      
      var flagMot=false;      
      var msg="Seleccione un motivo";
      $(".rbt_motivo").each(function(e){
        if($(this).prop("checked")==true){
          flagMot=true;
        }
      })

      if(flagMot==false){
        $("#lbl_msgMotivar").html(msg); 
        return false
        } 
     
    alert('motiva ');
    $.mobile.changePage( "#pageRecojosMain", { transition: "slidedown", changeHash: false });
   }


     function loginValidar(username, password){
        if (username.length === 0 || password.length === 0) {
            $("#lbl_msgLogin").html('Por favor, ingrese su usuario y password');
            /*mascara*/
            mask.loader( "hide" );
            return false;
        }
        $.ajax({
            url : 'http://www.olva.com.pe/eeduardo/serviceMovil.php',
            jsonp: "LoginCallback",
            dataType: "jsonp",
            data: {
               format: "json",
               username:username,
               password:password,
               funcion:'dLoginValidar'
            },
            success: function( result ) {
          obj_listado=new Array();;
               var resultado=result[0].resultado;
               if(resultado==1){/*hacer un each y OBtener las filas de los recojos*/   

                       var recojosCant=result.length;    
                   $("#recojosLista").html('')
                        jQuery.each( result, function( i, obj ) {
                   var ope_nombre=obj.ope_nombre ? obj.ope_nombre : null;
                   var ope_apellido=  obj.ope_apellido ? obj.ope_apellido : null;
                   var ope_codigo=obj.ope_codigo ? obj.ope_codigo : null;  
                   var ope_codacc=obj.ope_codacc ? obj.ope_codacc : null;  
                   var nro_recojo=obj.nro_recojo ? obj.nro_recojo : null;  
                   var ruc_dni=obj.ruc_dni ? obj.ruc_dni : null;  
                   var nom_cli=obj.nom_cli ? obj.nom_cli : null;  
                   var nro_cliente=obj.nro_cliente ? obj.nro_cliente : null;  
                   var dir_cliente=obj.dir_cliente ? obj.dir_cliente : null;  
                   var peso_envio=obj.peso_envio ? obj.peso_envio : null;  
                   var glosa=obj.glosa ? obj.glosa : null;  
                   var estado_envio=obj.estado_envio ? obj.estado_envio : null;  
                   var estado_recojo=obj.estado_recojo ? obj.estado_recojo : null;  
                   var flg_collect=obj.flg_collect ? obj.flg_collect : null;  
                   var cod_ciudad=obj.cod_ciudad ? obj.cod_ciudad : null;  
                   var contacto=obj.contacto ? obj.contacto : null;  
                   var tipo_recojo=obj.tipo_recojo ? obj.tipo_recojo : null;  
                   var sector_recojo=obj.sector_recojo ? obj.sector_recojo : null;  
                   var referencia=obj.referencia ? obj.referencia : null;  
                   var hora_recojo=obj.hora_recojo ? obj.hora_recojo : null;  
                   var hora_recojo_fin=obj.hora_recojo_fin ? obj.hora_recojo_fin : null; 
                   var param=parseInt(nro_recojo);           
                    
                  // alert(ope_codigo+'-'+nro_recojo);
                    obj_listado[i]={'ope_nombre':ope_nombre, 
                                    'ope_apellido':ope_apellido,
                                    'ope_codigo':ope_codigo,
                                    'ope_codacc':ope_codacc,
                                    'nro_recojo':nro_recojo,
                                    'ruc_dni':ruc_dni, 
                                    'nom_cli':nom_cli, 
                                    'nro_cliente':nro_cliente, 
                                    'dir_cliente':dir_cliente,
                                    'peso_envio':peso_envio, 
                                    'glosa':glosa,
                                    'estado_envio':estado_envio,
                                    'estado_recojo':estado_recojo,
                                    'flg_collect':flg_collect,
                                    'cod_ciudad':cod_ciudad,
                                    'contacto':contacto,
                                    'tipo_recojo':tipo_recojo,
                                    'sector_recojo':sector_recojo,
                                    'referencia':referencia,
                                    'hora_recojo':hora_recojo,
                                    'hora_recojo_fin':hora_recojo_fin}
                                   // alert(dir_cliente);

                     $("#recojosLista").append('<li><a href="#" onclick="linkrecojo('+param+');">'+nro_recojo+' - '+nom_cli+'</a></li>');  
                        });
               /*debo guardar los datos en la memoria del telefono junto con el listado del recojo y pasa al Menu Principal*/  
               usuario_global=username;
               password_global=password;
               $("#txt_username").val('');
               $("#txt_password").val('');
               $("#total_pendientes").html(recojosCant);
               //$("#total_recojos").html(recojosCant);
               cargaMotivos();
               //$.mobile.changePage( "#pageRecojosMain", { transition: "slidefade", changeHash: false }); 
               }else{  /*no se obtiene nada*/           
                   $("#lbl_msgLogin").html('Por favor, ingrese las credenciales correctas');       
               }
        }/*fin de success login*/

        });
     }

   function cargaMotivos(){

    $.ajax({
        url : 'http://www.olva.com.pe/eeduardo/serviceMovil.php',
        jsonp: "MotCallback",
        dataType: "jsonp",
        data: {
           format: "json",
             funcion:'dMotivosGet'
        },
        success: function( result ) {
          obj_motivos='';
          obj_motivos=new Array();
           var resultado=result[0].resultado;
               if(resultado==1){/*hacer un each y OBtener las filas de los motivos*/   
          jQuery.each( result, function( i, obj ) {
           var mot_codigo=obj.codigo ? obj.codigo : null;
           var mot_descripcion= obj.descripcion ? obj.descripcion : null;

           obj_motivos[i]={'mot_codigo':mot_codigo, 
                            'mot_descripcion':mot_descripcion}  

           //$("#motivarLista").append('<li><a href="#" onclick="motivarRecojo('+mot_codigo+');">'+mot_descripcion+'</a></li>');  
            $("#motivos_opcion").append(
              '<input  type="radio" name="radio-choice" class="rbt_motivo" id="radio-'+i+'" value="'+mot_codigo+'"/><label for="radio-'+i+'">'
              +mot_descripcion+'</label>');
        });
    

          /*guardar la informacion de motivos en la memoria del telefono*/ 
          

               $.mobile.changePage("#pageMenuPrincipal", { transition: "slide", changeHash: false }); // descomentar              
              


               }else{  /*no se obtiene nada*/         
                   //$("#lbl_msgLogin").html('Por favor, ingrese las credenciales correctas');       
               }
          

        }

    });

   }
/*EVENTOS DE PAGINAS */

$("#pageRecojosMain").on("pagebeforeshow", function( event ) {
    $("#recojosLista").listview();
    $("#recojosLista").listview('refresh');
})
$("#pageMotivar").on("pagebeforeshow", function( event ) {  
    $(".chk_orden").checkboxradio();
    $(".rbt_motivo").attr('checked',false).checkboxradio("refresh");
})
$("#pageIngresarOrden").on("pagebeforeshow", function( event ) {  
    $(".chk_orden").attr('checked',true);
      $(".chk_orden").each(function(e){        
        if($(this).prop('checked')==true){    
          $(this).parent().remove();/*debemos eliminar al padre ya que el es el contenedor*/
        }        
      })
      $("#txt_emiOrden").focus();
})


/*if(trim(usuario_global)=='' || password_global=''){
   //$.mobile.changePage( "#pageLogin" ); //evento setactivepage 

}*/
});

