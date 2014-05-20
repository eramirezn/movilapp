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
        <link rel="stylesheet" type="text/css" href="css/estilos.css">
        <script type="text/javascript" src="js/jquery-1.11.1.min.js"></script>
        <script type="text/javascript" src="js/jQueryMobile/jquery.mobile-1.4.2.min.js"></script>
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
            <label type="text" id="lbl_msgLogin"></label>
            <input type="text" placeholder="Username" id="txt_username">
            <input type="password" placeholder="Password" id="txt_password">
            <input type="button" data-theme="a" value="Log In" id="btnLogin">  
        </form>
    </div><!-- /content -->
</div><!-- /page -->
<div data-role="page" id="pageMenuPrincipal" data-theme="a">
    <div data-role="header" data-theme="b">
         <label type="text" id="lbl_operador"></label>
         <input type="button" id="btn_logOff" value="Log Off">  
        <h1>Menu Principal</h1>
    </div><!-- /header -->
    <div role="main" class="ui-content">
         <input type="button" id="btn_opcionDist" data-theme="a" value="Distribucion">  
         <input type="button" id="btn_opcionReco" data-theme="c" value="Recojos">  
    </div><!-- /content -->
</div><!-- /page -->
<!-- Start of second page -->
<div data-role="page" id="pageRecojosMain">
    <div data-role="header" data-theme="b">
        <input type="button" id="btn_backToMenuMain" value="Atras">  

        <h1>Recojos Pendientes</h1>
    </div><!-- /header -->
    <div role="main" class="ui-content">
        <ul data-role="listview" data-inset="true" id="recojosLista" class="ui-alt-icon"></ul>      
        <span><h4>Recojos Pendientes: </h4></span>
        <span><h3 id="total_pendientes"></h3></span>
        <span><h4>Total Recojos: </h4></span>
        <span ><h3 id="total_recojos"></h3></span>
    </div>
</div><!-- /page -->
<div data-role="page" id="pageRecojosDetalle">
    <div data-role="header" data-theme="b">
        <input type="button"  id="btn_backToRecojosMain" value="Atras">  
        <h1>Detalle Recojo:</h1>
    </div><!-- /header -->
    <div role="main" class="ui-content" id='contentRecDet'>
        <span><h4>Nro Recojo:</h4></span>   
        <span><h4 id="numrec_det">Nro Recojo:</h4></span> 
        <span><h4>Cliente:</h4></span>
        <span><h4 id="nomcli_det"></h4></span>
        <span><h4>Ruc:</h4></span>  
        <span><h4 id="ruc_det">Ruc:</h4></span>  
        <span><h4>Contacto:</h4></span>
        <span><h4 id="contacto_det">Contacto:</h4></span>
        <span><h4>Direccion:</h4></span>    
        <span><h4 id="dirrec_det">Direccion:</h4></span>    
        <span><h4>Peso:</h4></span> 
        <span><h4 id="pesorec_det">Peso:</h4></span> 
        <span><h4>Glosa:</h4></span>    
        <span><h4 id="glosa_det">Glosa:</h4></span>    
        <span><h4>Estado Envio:</h4></span> 
        <span><h4 id="estado_envio_det">Estado Envio:</h4></span> 
        <span><h4>Estado Recojo:</h4></span>    
        <span><h4 id="estado_recojo_det">Estado Recojo:</h4></span>    
        <span><h4>Hora Recojo</h4></span>   
        <span><h4 id="_horarec_det">Hora Recojo</h4></span>   
        <span><h4>Hora Recojo Final:</h4></span>    
        <span><h4 id="horafin_det">Hora Recojo Final:</h4></span>    
         <fieldset class="ui-grid-a">
                    <div class="ui-block-a"><input type="button" id="btn_confirmaRec" data-theme="b" value="Confirmar"></div>
                    <div class="ui-block-b"><input type="button" id="btn_motivaRec" data-theme="b" value="Motivar"> </div>
        </fieldset>
    </div>
</div>
<div data-role="page" id="pageRecojosMain">
    <div data-role="header" data-theme="b">
        <input type="button" id="btn_backToMenuMain" value="Atras"> 
        <h1>Motivar recojo</h1>
    </div>
    <div role="main" class="ui-content">
        <ul data-role="listview" data-inset="true" id="recojosLista" class="ui-alt-icon"></ul>      
        
    </div>
</div>



        <script type="text/javascript" src="cordova.js"></script>
        <script type="text/javascript" src="js/index.js"></script>
        <script type="text/javascript">
            app.initialize();
        </script>
    </body>
</html>
------------------------
 var obj_listado= new Array();
function linkrecojo(param){

  $.mobile.changePage( "#pageRecojosDetalle", { transition: "slide", changeHash: false });

  //alert(param)

  $("#nomcli_det").html('');
  $("#ruc_det").html('');
  $("#contacto_det").html('');
  $("#numrec_det").html('');
  $("#dir_cliente").html('');
  $("#peso_envio").html('');
  $("#glosa").html('');
  $("#estado_envio").html('');
  $("#hora_recojo").html('');
  $("#hora_recojo_fin").html('');

  jQuery.each(obj_listado, function( i, obj ) {
    if(parseInt(obj.nro_recojo)==parseInt(param)){ /*cuando coincide el recojo seleccionado*/     
      //alert(obj.nom_cli+'-'+obj.ruc_dni+'-'+obj.contacto+'-'+obj.nro_recojo+'-'+obj.dir_cliente+'-'+obj.nom_cli+'-'+obj.peso_envio+'-'+
      //obj.glosa+'-'+obj.estado_envio+'-'+obj.hora_recojo+'-'+obj.hora_recojo_fin)
      $("#nomcli_det").html(obj.nom_cli);
      $("#ruc_det").html(obj.ruc_dni);
      $("#contacto_det").html(obj.contacto);
      $("#dirrec_det").html(obj.dir_cliente);
      $("#pesorec_det").html(obj.peso_envio);
      $("#glosa_det").html(obj.glosa);
      $("#estado_envio_det").html(obj.estado_envio);
      $("#estado_recojo_det").html(obj.hora_recojo);
      $("#horafin_det").html(obj.hora_recojo_fin);
    }
  });
}





$(document).ready(function(){
 
	$( "#btnLogin" ).click(function() {
  	  $("#lbl_msgLogin").html('');
	  var username=$("#txt_username").val();
	  var password=$("#txt_password").val();
	  loginValidar(username, password);
	});
	$("#btn_opcionReco").click(function (){		
        $.mobile.changePage( "#pageRecojosMain", { transition: "slide", changeHash: false });
	})
	$("#btn_logOff").click(function (){		
        /*destruimos las credenciales*/
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
		alert('seguro??')
	})
	$("#btn_motivaRec").click(function (){   
    alert('seguro??')
  })












	 function loginValidar(username, password){
        if (username.length === 0 || password.length === 0) {
            $("#lbl_msgLogin").html('Por favor, ingrese su usuario y password');
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
		       var resultado=result[0].resultado;
               if(resultado==1){/*hacer un each y OBtener las filas de los recojos*/   

  			   var recojosCant=result.length;           
           $("#recojosLista").html('');
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
           var flg_collect=obj.flg_collect ? obj.flg_collect : null;  
           var cod_ciudad=obj.cod_ciudad ? obj.cod_ciudad : null;  
           var contacto=obj.contacto ? obj.contacto : null;  
           var tipo_recojo=obj.tipo_recojo ? obj.tipo_recojo : null;  
           var sector_recojo=obj.sector_recojo ? obj.sector_recojo : null;  
           var referencia=obj.referencia ? obj.referencia : null;  
           var hora_recojo=obj.hora_recojo ? obj.hora_recojo : null;  
           var hora_recojo_fin=obj.hora_recojo_fin ? obj.hora_recojo_fin : null; 
           var param=parseInt(nro_recojo);           
            
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
                            'flg_collect':flg_collect,
                            'cod_ciudad':cod_ciudad,
                            'contacto':contacto,
                            'tipo_recojo':tipo_recojo,
                            'sector_recojo':sector_recojo,
                            'referencia':referencia,
                            'hora_recojo':hora_recojo,
                            'hora_recojo_fin':hora_recojo_fin}
                            alert(dir_cliente);

           $("#recojosLista").append('<li><a href="#" onclick="linkrecojo('+param+');">'+nro_recojo+' - '+nom_cli+'</a></li>');  
				});
    


               /*debo guardar los datos en la memoria del telefono junto con el listado del recojo y pasa al Menu Principal*/  
               $("#txt_username").val('');
               $("#txt_password").val('');
               $("#total_pendientes").html('');
               $("#total_recojos").html(recojosCant);
               $.mobile.changePage( "#pageMenuPrincipal", { transition: "slide", changeHash: false }); // descomentar              
               //$.mobile.changePage( "#pageRecojosMain", { transition: "slidefade", changeHash: false });                  


               }else{  /*no se obtiene nada*/       	
                   $("#lbl_msgLogin").html('Por favor, ingrese las credenciales correctas');       
               }
		    

        }

		});
	 }

});
