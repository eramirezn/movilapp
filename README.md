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
        <script type="text/javascript" src="cordova.js"></script>
        <script type="text/javascript" src="js/app.js"></script>
        <script type="text/javascript" src="js/funciones.js"></script>
        <title>Operador Olva App</title>
    </head>
    <body>
        <input type="hidden" id="hid_nrorecojo" value=""/>
        <input type="hidden" id="hid_cod_operador"  value=""/>
        <div class="app">
            <h1>Olva App</h1>
            <div id="deviceready" class="blink">
                <p class="event listening"></p>
                <p class="event received"></p>
            </div>
        </div>
        <div data-role="page" id="pageLogin">

            <div data-role="header"  data-position="fixed"  data-theme="b" data-position="fixed">
                <h1>Autenticacion</h1>
            </div><!-- /header -->

            <div role="main" class="ui-content">
                <h4>Iniciar Sesion:</h4>
                <form>
                    <label type="text" id="lbl_msgLogin" class="alertHid"></label>
                    <input type="text" placeholder="Username" id="txt_username">
                    <input type="password" placeholder="Password" id="txt_password">
                    <input type="button" data-theme="a" data-icon="home" id="btnLogin" value="Log In" >  
                </form>
            </div><!-- /content -->
        </div><!-- /page -->
        <div data-role="page" id="pageMenuPrincipal" data-theme="a">
            <div data-role="header"  data-position="fixed" data-theme="b">
                 <label type="text" id="lbl_operador"></label>
                 <!--<input type="button" id="btn_logOff" value="Log Off">  -->
                <a href="#" data-theme="b" data-direction="reverse" id="btn_logOut" data-icon="back">Log Out</a> 
                <h1></h1>
            </div><!-- /header -->
            <div role="main" class="ui-content">
                 <input type="button" id="btn_opcionDist" data-icon="grid" data-theme="a" value="Distribucion">  
                 <input type="button" id="btn_opcionReco" data-icon="grid" data-theme="c" value="Recojos">  

            </div><!-- /content -->
        </div><!-- /page -->
        <!-- Start of second page -->
        <div data-role="page" id="pageRecojosMain">
            <div data-role="header"  data-position="fixed" data-theme="b">
                <!--<input type="button" id="btn_backToMenuMain" value="Atras">  -->
                <a href="#pageMenuPrincipal" data-theme="b" data-direction="reverse" data-icon="back">Atras</a> 
                <h1></h1>
            </div><!-- /header -->
            <div role="main" class="ui-content">    
                 <input type="button" id="btn_actualDatosRec" data-icon="grid" data-theme="c" value="Actualizar">  
                <h4 class="alertHid">Recojos Pendientes:</h4>
                <ul data-role="listview" data-inset="true"  id="recojosLista" class="ui-alt-icon"></ul>  


                <div class="ui-grid-a ui-bar ui-bar-e" data-theme="b">
                    <div class="ui-block-a">
                        <strong class="alertHid">Total:</strong><strong class="alertHid" id="txt_total_pendientes"></strong>
                    </div>
                    <div class="ui-block-b">
                        <!--<div><strong>Total:</strong></div>
                        <div><strong id="total_recojos"></strong></div>-->
                    </div>
                </div>
            </div>
        </div>
        <div data-role="page" id="pageRecojosDetalle">
            <div data-role="header" data-position="fixed" data-theme="b">
                <!--<input type="button"  id="btn_backToRecojosMain" value="Atras"> -->
                <a href="#pageRecojosMain" data-theme="b" data-direction="reverse" data-icon="back">Atras</a> 
                <h1></h1>
            </div><!-- /header -->
            <div role="main" class="ui-content" id='contentRecDet'>
            <h1 class="alertHid"></h1><strong class="alertHid" id="txt_nro_recojo"></strong>
             <fieldset class="ui-grid-a">
                        <div class="ui-block-a" style="font-weight:normal; font-size:0.7em;">
                            <input type="button" id="btn_confirmaRec" data-mini="true" data-icon="check" data-theme="a" value="Confirmar">
                        </div>
                        <div class="ui-block-b" style="font-size:0.7em;">
                            <input type="button" id="btn_motivaRec" data-mini="true" data-icon="delete" data-theme="a" value="Motivar"> 
                        </div>
            </fieldset>
            
                <h4 id="collect_det" class="alertHid"></h4>
            <ul data-role="listview"  data-inset="true" id="detalleLista" class="ui-alt-icon">
                <li data-role="list-divider" class="headerList">Cliente:</li>
                <li id="nomcli_det" style="white-space:normal; font-size:0.7em;"></li>
                <li data-role="list-divider" class="headerList">Tipo:</li>
                <li id="tipocliente_det" style="white-space:normal; font-size:0.7em;"></li>
                <li data-role="list-divider" class="headerList">Ruc:</li>
                <li id="ruc_det" style="white-space:normal; font-size:0.7em;"></li>
                <li data-role="list-divider" class="headerList">Contacto:</li>
                <li id="contacto_det" style="white-space:normal; font-size:0.7em;"></li>
                <li data-role="list-divider" class="headerList">Direccion:</li>
                <li id="dirrec_det" style="white-space:normal; font-size:0.7em;"></li>
                <li data-role="list-divider" class="headerList">Peso:</li>
                <li id="pesorec_det" style="white-space:normal; font-size:0.7em;"></li>
                <li data-role="list-divider" class="headerList">Glosa:</li>
                <li id="glosa_det" style="white-space:normal; font-size:0.7em;"></li>
                <!--<li data-role="list-divider"><h4>Estado Envio:</h4></li>
                <li ><h4 id="estado_envio_det"></h4></li>-->
                <li data-role="list-divider" class="headerList">Estado Recojo:</li>
                <li id="estado_recojo_det" style="white-space:normal; font-size:0.7em;"></li>
                <li data-role="list-divider" class="headerList">Hora Recojo:</li>
                <li id="_horarec_det" style="white-space:normal; font-size:0.7em;"></li>
                <li data-role="list-divider" class="headerList">Hora Recojo Final:</li>
                <li id="horafin_det" style="white-space:normal; font-size:0.7em;"></li>
            </ul> 

        </div>
        </div>
        <div data-role="page" id="pageMotivar">
            <div data-role="header"  data-position="fixed" data-theme="b">
                <!--<input type="button" id="btn_backToRecojDet" value="Atras"> -->
                <a href="#pageRecojosDetalle" data-theme="b" data-direction="reverse" data-icon="back">Atras</a> 
                <h1></h1>
            </div>
            <div role="main" class="ui-content">
                <h4 class="alertHid">Elija un motivo:</h4>
                <fieldset data-role="controlgroup" id='motivos_opcion'></fieldset>      
                <div id="lbl_msgMotivar" class="alertHid"></div> 
                <div  style="font-size:0.7em;">
                    <input type="button" data-theme="a" data-icon="check" value="Aceptar" id='btn_aceptaMotivar'/>  
                </div>           
            </div>

        </div>

        <div data-role="page" id="pageIngresarOrden">
            <div data-role="header"  data-position="fixed" data-theme="b">
                <!--<input type="button" id="btn_backToRecojDet" value="Atras"> -->
                <a href="#pageRecojosDetalle" data-theme="b" data-direction="reverse" data-icon="back">Atras</a> 
                <h1></h1>
            </div>
            <div role="main" class="ui-content">
                <h5 class="alertHid">Nro Documento:</h5>   
                <fieldset   class="ui-grid-a">         
                    <div id="div_txt_emiOrden" class="ui-block-a"><input type="text" placeholder="Emision" id="txt_emiOrden"></div>
                    <div id="div_txt_numOrden" class="ui-block-b"><input type="text" placeholder="Numero" id="txt_numOrden"></div>
                </fieldset>
                <fieldset   id="btnAddRmvDoc" class="ui-grid-a">         
                    <div class="ui-block-a center" style="font-size:0.7em;">
                        <input class="botonera_orden" type="button" id="btn_addOrden" data-icon="plus" value="Agregar" data-theme="a">
                    </div>
                    <div class="ui-block-b center" style="font-size:0.7em;">
                        <input class="botonera_orden"  style="font-size:0.7em;" type="button" id="btn_delOrden" data-icon="minus"  value="Quitar" data-theme="a">
                    </div>
                </fieldset> 
                <h5 class="alertHid">Documentos a anexar para este recojo:</h5>
                <fieldset data-role="controlgroup" id="ordenesListChk">
                   <!--<input type="checkbox" name="checkbox-2" id="checkbox-2" class="custom" /><label for="checkbox-2">I agree</label>-->
                </fieldset>
                <!--<ul data-role="listview" data-inset="true"  id="ordenesLista" class="ui-alt-icon">
                </ul>-->
                <div id="div_btnAceptaConfirmar"  style="font-size:0.7em;">
                    <input type="button"  data-theme="a" data-icon="check" value="Aceptar" id='btn_aceptaConfirmar'/>
                </div>
            </div>

        </div>
    </body>
</html>



INDEX.HTML
---------------------------------


function trim(string)
{
    for(i=0; i<string.length; )
    {
        if(string.charAt(i)==" ")
            {string=string.substring(i+1, string.length);}
        else
            {break;}
    }
    for(i=string.length-1; i>=0; i=string.length-1)
    {
        if(string.charAt(i)==" ")
            {string=string.substring(0,i);}
        else
            {break;}
    }
    return string;
}


FUNCIONASGLOBALES
--------------------------

app.initialize();   

 var obj_listado='';
 var obj_motivos='';
 var usuario_global='';
 var password_global='';
 var obj_solicPendientes=new Array();
 var mask;

function linkrecojo(nrorec){/*REALIZA LAS VALIDACIONES Y CARGA DE LA LISTA DEL DETALLE DE RECOJO*/


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
  $("#collect_det").html('');
  $("#tipocliente_det").html('');  
   var objRecojo=getDatosRecojo(obj_listado,nrorec);/*busca un obj especifico dentro de un array*/
  if(objRecojo!=false){

      var collect_flag;
      var hora_ini='';
      var hora_fin='';
      var estado_rec='';

      if (objRecojo.flg_collect==1){
        collect_flag="COLLECT";
      }else{
        collect_flag="";
      }
     /*AGREGAMOS LOS : A LOS CAMPOS DE HORA */
      if((objRecojo.hora_recojo)!=null && (objRecojo.hora_recojo)!=undefined ){
       hora_ini=(objRecojo.hora_recojo).substring(0,2)+':'+(objRecojo.hora_recojo).substring(2,4);
      }
      if((objRecojo.hora_recojo_fin)!=null && (objRecojo.hora_recojo_fin)!=undefined){
       hora_fin=(objRecojo.hora_recojo_fin).substring(0,2)+':'+(objRecojo.hora_recojo_fin).substring(2,4);    
      }
      /*MOSTRAR EL ESTADO DE RECOJO SEGUN EL CODIGO OBTENIDO*/
      switch (parseInt(objRecojo.estado_recojo)){
         case 0 : estado_rec="Pendiente";  break;
         case 1 : estado_rec="Asignado";  break;
         case 2 : estado_rec="Recogido";  break;
         case 3 : estado_rec="Anulado";  break;
         case 4 : estado_rec="Retenido";  break;
         case 5 : estado_rec="Despachado";  break;
         case 6 : estado_rec="Devuelto";  break;
         case 7 : estado_rec="Pendiente-Postergado";  break;
         default: estado_rec="";  break;
      }


     /*CARGAMOS LA LISTA DEL DETALLE CON LA INFORMACION TRATADA*/
      $("#txt_nro_recojo").html('');
      $("#txt_nro_recojo").html('Recojo Nro: '+parseInt(objRecojo.nro_recojo));
      //$("#numrec_det").html(objRecojo.nro_recojo);
      $("#nomcli_det").html(objRecojo.nom_cli);
      $("#ruc_det").html(objRecojo.ruc_dni);
      $("#contacto_det").html(objRecojo.contacto+' / '+objRecojo.telefono);
      $("#dirrec_det").html(objRecojo.dir_cliente);
      $("#pesorec_det").html(objRecojo.peso_envio);
      $("#glosa_det").html(objRecojo.glosa);
      //$("#estado_envio_det").html(objRecojo.estado_envio);
      $("#estado_recojo_det").html(estado_rec);
      $("#_horarec_det").html(hora_ini);
      $("#horafin_det").html(hora_fin);
      $("#collect_det").html(collect_flag);
      $("#tipocliente_det").html(objRecojo.des_tipo);

      $("#hid_nrorecojo").val(parseInt(nrorec));
      $("#hid_cod_operador").val(objRecojo.ope_codigo);
      $("#hid_ruc_dni_cliente").val(objRecojo.ruc_dni);
      $("#hid_nro_cliente").val(objRecojo.nro_cliente);

   }

   $.mobile.changePage( "#pageRecojosDetalle", { transition: "slide", changeHash: false });
}


function getDatosRecojo(objBusq,nrorecojo){
   var objRecojoBusqueda={};
   var flg=false;
   jQuery.each(objBusq, function( i, obj ) {/*BUSCO EL NRO DE RECOJO ELEGIDO EN DENTRO DEL OBJETO DONDE GUARDE LOS RECOJOS*/
      /*VALIDAMOS SI SE MUESTRA EL MENSAJE DE COLLECT*/
         if(parseInt(obj.nro_recojo)==parseInt(nrorecojo)){ 
            objRecojoBusqueda={'ope_nombre':obj.ope_nombre, 
                              'ope_apellido':obj.ope_apellido,
                              'ope_codigo':obj.ope_codigo,
                              'ope_codacc':obj.ope_codacc,
                              'nro_recojo':obj.nro_recojo,
                              'ruc_dni':obj.ruc_dni, 
                              'nom_cli':obj.nom_cli, 
                              'nro_cliente':obj.nro_cliente, 
                              'dir_cliente':obj.dir_cliente,
                              'peso_envio':obj.peso_envio, 
                              'glosa':obj.glosa,
                              'estado_envio':obj.estado_envio,
                              'estado_recojo':obj.estado_recojo,
                              'flg_collect':obj.flg_collect,
                              'cod_ciudad':obj.cod_ciudad,
                              'contacto':obj.contacto,
                              'tipo_recojo':obj.tipo_recojo,
                              'sector_recojo':obj.sector_recojo,
                              'referencia':obj.referencia,
                              'hora_recojo':obj.hora_recojo,
                              'hora_recojo_fin':obj.hora_recojo_fin,
                              'tip_cliente':obj.tip_cliente,
                              'des_tipo':obj.des_tipo,
                              'telefono':obj.telefono,
                              'fec_recojo':obj.fec_recojo,
            } 
            flg=true;   
         }
  });

         if(flg==true){
            return objRecojoBusqueda;
         }else{
            return false;
         } 
}


$(document).ready(function(){
  verificarSesion();
 
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
      logOut();
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
	   guardaRecojoConfirmado();
    //$.mobile.changePage( "#pageRecojosMain", { transition: "slidedown", changeHash: false });
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
  $("#btn_actualDatosRec").click(function (){   
      $("#recojosLista").html('');   
                dRecojosListGet();   
               // $.mobile.changePage( "#pageRecojosMain", { transition: "slidedown", changeHash: false });  
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
          '<label><input type="checkbox" class="chk_orden" name="checkbox-1" id="checkbox-1" value="'+txt_emision+'_|_'+txt_numero+'" />'+txt_emision+' - '+txt_numero+'</label>');
       }
       //$("#ordenesLista").listview('refresh');
       $("#txt_emiOrden").val(14);
       $("#txt_numOrden").val('');
       $(".chk_orden").checkboxradio();
       $(".chk_orden").checkboxradio("refresh");
       $(".chk_orden").attr('checked',false).checkboxradio("refresh");
       txt_emiOrden
  })


  $("#btn_delOrden").click(function (){
      $(".chk_orden").each(function(e){        
        if($(this).prop('checked')==true){    
          $(this).parent().remove();/*debemos eliminar al padre ya que el es el contenedor*/
        }        
      })
  })

     





/*EVENTOS DE PAGINAS */

$("#pageRecojosMain").on("pagebeforeshow", function( event ) {
    $("#recojosLista").listview();
    $("#recojosLista").listview('refresh');
})
$("#pageMotivar").on("pagebeforeshow", function( event ) {  
    $(".rbt_motivo").checkboxradio();
    $(".rbt_motivo").attr('checked',false).checkboxradio("refresh");
})
$("#pageIngresarOrden").on("pagebeforeshow", function( event ) {  
    $("#txt_emiOrden").val(14);
})
$("#pageIngresarOrden").on("pagebeforeshow", function( event ) {  
    $(".chk_orden").attr('checked',true);
      $(".chk_orden").each(function(e){        
        if($(this).prop('checked')==true){    
          $(this).parent().remove();/*debemos eliminar al padre ya que el es el contenedor*/
        }        
      })
})
$('#pageRecojosMain').bind('pageshow', function() {
      listRecojoRefreshStyle();
    });


/*
$("#pageRecojosMain").pagecontainer("load", function( event ) { 
    alert('load')
 })

$( "#pageRecojosMain" ).on( "pagecontainershow", function( event, ui ) {
alert( "This page was just hidden: " + ui.prevPage );
});
$(document).on('pagecontainershow', function(e, ui) {
    var pageId = $('body').pagecontainer('getActivePage').prop('id');
    alert(pageId);
});
$(":mobile-pagecontainer").on("pagecontainershow", function( event, ui ) {
alert( "This page was just hidden: " + ui.prevPage );
});

*/



/*FUNCIONES*/
    function validarMotivosSeleccionado(){
      var flagMot=false;      
          var msg="Seleccione un motivo";   
          $(".rbt_motivo").each(function(e){
            if($(this).prop("checked")==true){
              flagMot=true;
            }
          })

          if(flagMot==false){
            $("#lbl_msgMotivar").html(msg); 
            return false;
          }else{
            return true;
          }
    }

    function motivarRecojo(){ 

      rptaMotivos=validarMotivosSeleccionado();
      if(rptaMotivos==false){
        return false;
      }
      var estadoConexion=app.checkConnection(); 
      alert(estadoConexion)

      var hid_nrorecojo=$("#hid_nrorecojo").val();
      var objRecojo=getDatosRecojo(obj_listado, hid_nrorecojo);
      var codDigitador=objRecojo.ope_codigo
      var nro_recojo=objRecojo.nro_recojo
      var ope_codigo=objRecojo.ope_codigo
      var fec_recojo=objRecojo.fec_recojo
      var estado=0;
      var create_hostName='WEB';
      var parametros={
              'funcion'           :'dMotivarRecojo',
              'codDigitador'      :codDigitador,
              'nro_recojo'        :nro_recojo,
              'ope_codigo'        :ope_codigo,
              'fec_recojo'        :fec_recojo,
              'estado'            :estado,
              'create_hostName'   :create_hostName,
              'ordenesString'     :"",
              'ruc_dni'           :"",
              'nro_cliente'       :"",
              'cod_ciudad'        :""  
            }

      if(estadoConexion!=false){        
        alert('No se detecto una conexion a internet, la solicitud se almacenara y se enviara cuando se conecte a una red valida'); 
        var i=obj_solicPendientes.length;
        obj_solicPendientes[i]=parametros;
        /*guarda en local storage*/
        var listSolicPendientesLS =JSON.stringify(obj_solicPendientes);
        localStorage.setItem('listSolicPendientesLS', listSolicPendientesLS);
        $.mobile.changePage( "#pageRecojosMain", { transition: "slidedown", changeHash: false });  

      }else{
        ejecutarConsultaMotivarRecojo(parametros);
      }       
   }/*FIN motivarRecojo*/

    function ejecutarConsultaMotivarRecojo(parametros){   
     /* alert(parametros.codDigitador)
      alert(parametros.nro_recojo)
      alert(parametros.ope_codigo)
      alert(parametros.fec_recojo)
      alert(parametros.estado)
      alert(parametros.create_hostName)
    return false; */  
      $.ajax({
         url : 'http://www.olva.com.pe/WS_JSONP/cn/nOpeRecojos.php',
         jsonp: "callbackRecojos",
         dataType: "jsonp",
         data: {
              format: "json",
              funcion:'dMotivarRecojo',
              vs_var1:parametros.codDigitador,
              vs_var2:parametros.nro_recojo,
              vs_var3:parametros.ope_codigo,
              vs_var4:parametros.fec_recojo,
              vs_var5:parametros.estado,
              vs_var6:parametros.create_hostName,
          },
          success: function( result ) {
            var resultado=result[0].resultado;
              if(resultado==1){
                alert(result[0].respuesta)/*llamar al encargado de actualizar la lista*/
                dRecojosListGet();
                cargaListadoRecojos();
                $.mobile.changePage( "#pageRecojosMain", { transition: "slidedown", changeHash: false });  
              }else{
                alert(result[0].respuesta)
                dRecojosListGet();
                cargaListadoRecojos();
                $.mobile.changePage( "#pageRecojosMain", { transition: "slidedown", changeHash: false });
              }
          }
      });    
    }


    function listRecojoRefreshStyle(){
      $("#recojosLista").listview();
      $("#recojosLista").listview('refresh');
    }

   function guardaRecojoConfirmado(){
      /*comprobar si hay o no ordenes anexadas */
      var estadoConexion=app.checkConnection(); 
      alert(estadoConexion)

      var hid_nrorecojo=$("#hid_nrorecojo").val();
      var objRecojo   =getDatosRecojo(obj_listado, hid_nrorecojo);
      var codDigitador=objRecojo.ope_codigo;
      var nro_recojo  =objRecojo.nro_recojo;
      var ope_codigo  =objRecojo.ope_codigo;
      var fec_recojo  =objRecojo.fec_recojo;
      var ruc_dni     =objRecojo.ruc_dni;
      var nro_cliente =objRecojo.nro_cliente;
      var cod_ciudad  =objRecojo.cod_ciudad;
      var estado=2;
      var create_hostName='WEB';
      var ordenesString='';
      $(".chk_orden").each(function(e){
        ordenesString+=e>0?'_||_':'';
        ordenesString+=$(this).val();
      })
      var parametros={
              'funcion'           :'dConfirmarRecojo',
              'codDigitador'      :codDigitador,
              'nro_recojo'        :nro_recojo,
              'ope_codigo'        :ope_codigo,
              'fec_recojo'        :fec_recojo,
              'estado'            :estado,
              'create_hostName'   :create_hostName,
              'ordenesString'     :ordenesString,
              'ruc_dni'           :ruc_dni,
              'nro_cliente'       :nro_cliente,
              'cod_ciudad'        :cod_ciudad  
            }

      if(estadoConexion!=false){
        alert('No se detecto una conexion a internet, la solicitud se almacenara y se enviara cuando se conecte a una red valida');    
        var i=(obj_solicPendientes.length);       
        obj_solicPendientes[i]=parametros;
            /*guarda en local storage*/
            var listSolicPendientesLS =JSON.stringify(obj_solicPendientes);
            localStorage.setItem('listSolicPendientesLS', listSolicPendientesLS);
            $.mobile.changePage( "#pageRecojosMain", { transition: "slidedown", changeHash: false });  
      }else{
        ejecutarConsultaConfirmarRecojo(parametros);      
      }

   }

   function ejecutarConsultaConfirmarRecojo(parametros){ 
      /*alert(parametros.codDigitador)
      alert(parametros.nro_recojo)
      alert(parametros.ope_codigo)
      alert(parametros.fec_recojo)
      alert(parametros.estado)
      alert(parametros.create_hostName)
      alert(parametros.ordenesString)
      alert(parametros.ruc_dni)
      alert(parametros.nro_cliente)
      alert(parametros.cod_ciudad)      
      return false;       */
      $.ajax({
         url : 'http://www.olva.com.pe/WS_JSONP/cn/nOpeRecojos.php',
         jsonp: "callbackRecojos",
         dataType: "jsonp",
         data: {
              format: "json",
              funcion:'dConfirmarRecojo',
              vs_var1:parametros.codDigitador,
              vs_var2:parametros.nro_recojo,
              vs_var3:parametros.ope_codigo,
              vs_var4:parametros.fec_recojo,
              vs_var5:parametros.estado,
              vs_var6:parametros.create_hostName,
              vs_var7:parametros.ordenesString,
              vs_var8:parametros.ruc_dni,
              vs_var9:parametros.nro_cliente,
              vs_var10:parametros.cod_ciudad
          },
          success: function( result ) {
            var resultado=result[0].resultado;
              if(resultado==1){
                alert(result[0].respuesta)/*llamar al encargado de actualizar la lista con web socket*/                
                dRecojosListGet();
                cargaListadoRecojos();
                $.mobile.changePage( "#pageRecojosMain", { transition: "slidedown", changeHash: false });  
              }else{
                alert(result[0].respuesta)
                dRecojosListGet();
                cargaListadoRecojos();
                $.mobile.changePage( "#pageRecojosMain", { transition: "slidedown", changeHash: false });
              }

          }
      }); 
   }


   function loginValidar(username, password){
        if (username.length === 0 || password.length === 0) {
            $("#lbl_msgLogin").html('Por favor, ingrese su usuario y password');
            /*mascara*/
            mask.loader("hide");
            return false;
        }
    $.ajax({
        url : 'http://www.olva.com.pe/WS_JSONP/cn/nOpeRecojos.php',
        jsonp: "callbackRecojos",
        dataType: "jsonp",
        data: {
           format: "json",
             username:username,
             password:password,
             funcion:'dLoginValidar'
        },
        success: function( result ) {
          obj_listado=new Array();
           var resultado=result[0].resultado;
               if(resultado==1){/*hacer un each y OBtener las filas de los recojos*/   


                   jQuery.each( result, function( i, obj ){
                   var ope_nombre=obj.ope_nombre;
                   var ope_apellido=  obj.ope_apellido;
                   var ope_codigo=obj.ope_codigo;  
                   var ope_codacc=obj.ope_codacc;  
                   var nro_recojo=obj.nro_recojo;  
                   var ruc_dni=obj.ruc_dni;  
                   var nom_cli=obj.nom_cli;  
                   var nro_cliente=obj.nro_cliente;  
                   var dir_cliente=obj.dir_cliente;  
                   var peso_envio=obj.peso_envio;  
                   var glosa=obj.glosa;  
                   var estado_envio=obj.estado_envio;  
                   var estado_recojo=obj.estado_recojo;  
                   var flg_collect=obj.flg_collect;  
                   var cod_ciudad=obj.cod_ciudad;  
                   var contacto=obj.contacto;  
                   var tipo_recojo=obj.tipo_recojo;  
                   var sector_recojo=obj.sector_recojo;  
                   var referencia=obj.referencia;  
                   var hora_recojo=obj.hora_recojo;  
                   var hora_recojo_fin=obj.hora_recojo_fin; 
                   var tip_cliente=obj.tip_cliente; 
                   var des_tipo=obj.des_tipo; 
                   var telefono=obj.telefono; 
                   var fec_recojo=obj.fec_recojo;   
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
                                    'hora_recojo_fin':hora_recojo_fin,
                                    'tip_cliente':tip_cliente,
                                    'des_tipo':des_tipo,
                                    'telefono':telefono,
                                    'fec_recojo':fec_recojo
                                  }
                  });
                cargaListadoRecojos(); 

                /*guarda en local storage*/
                var listRecojoLS =JSON.stringify(obj_listado);
                var usernameLS = trim(result[0].ope_codigo);
                var passwordLS = trim(result[0].ope_codacc);
                localStorage.setItem('listRecojoLS', listRecojoLS);
                localStorage.setItem('usernameLS', usernameLS);
                localStorage.setItem('passwordLS', passwordLS);


               usuario_global=username;
               password_global=password;
               $("#txt_username").val('');
               $("#txt_password").val('');
               getMotivosWebService();/*llama a la funcion que traera la info. de los motivos*/
               $.mobile.changePage( "#pageMenuPrincipal", { transition: "slidedown", changeHash: false });    
               }else if(resultado==2){  /*error en credenciales o conexion*/         
                  $("#lbl_msgLogin").html(result[0].respuesta); 
                  mask.loader("hide");
                  return false;      
               }else if(resultado==3){/*no hay recojos pendientes*/
                /*localstorage*/
                cargaListadoRecojos();
                var listRecojoLS =JSON.stringify(obj_listado);
                var usernameLS = trim(result[0].ope_codigo);
                var passwordLS = trim(result[0].ope_codacc);
                localStorage.setItem('listRecojoLS', listRecojoLS);
                localStorage.setItem('usernameLS', usernameLS);
                localStorage.setItem('passwordLS', passwordLS);

               usuario_global=username;
               password_global=password;
               $("#txt_username").val('');
               $("#txt_password").val('');
               getMotivosWebService();/*llama a la funcion que traera la info. de los motivos*/
               $.mobile.changePage( "#pageMenuPrincipal", { transition: "slidedown", changeHash: false });   
                mask.loader("hide");
                return false;      
               }
        }/*fin de success login*/

    });
   }/*FIN loginValidar*/

    function dRecojosListGet(){
    $.ajax({
        url : 'http://www.olva.com.pe/WS_JSONP/cn/nOpeRecojos.php',
        jsonp: "callbackRecojos",
        dataType: "jsonp",
        data: {
          format: "json",
          username:usuario_global,
          password:password_global,
          funcion:'dRecojosListGet'
        },
        success: function( result ) {
            obj_listado=new Array();
           var resultado=result[0].resultado;
               if(resultado==1){/*hacer un each y OBtener las filas de los recojos*/ 


                   jQuery.each( result, function( i, obj ){
                   var ope_nombre=obj.ope_nombre;
                   var ope_apellido=  obj.ope_apellido;
                   var ope_codigo=obj.ope_codigo;  
                   var ope_codacc=obj.ope_codacc;  
                   var nro_recojo=obj.nro_recojo;  
                   var ruc_dni=obj.ruc_dni;  
                   var nom_cli=obj.nom_cli;  
                   var nro_cliente=obj.nro_cliente;  
                   var dir_cliente=obj.dir_cliente;  
                   var peso_envio=obj.peso_envio;  
                   var glosa=obj.glosa;  
                   var estado_envio=obj.estado_envio;  
                   var estado_recojo=obj.estado_recojo;  
                   var flg_collect=obj.flg_collect;  
                   var cod_ciudad=obj.cod_ciudad;  
                   var contacto=obj.contacto;  
                   var tipo_recojo=obj.tipo_recojo;  
                   var sector_recojo=obj.sector_recojo;  
                   var referencia=obj.referencia;  
                   var hora_recojo=obj.hora_recojo;  
                   var hora_recojo_fin=obj.hora_recojo_fin; 
                   var tip_cliente=obj.tip_cliente; 
                   var des_tipo=obj.des_tipo; 
                   var telefono=obj.telefono; 
                   var fec_recojo=obj.fec_recojo;   
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
                                    'hora_recojo_fin':hora_recojo_fin,
                                    'tip_cliente':tip_cliente,
                                    'des_tipo':des_tipo,
                                    'telefono':telefono,
                                    'fec_recojo':fec_recojo
                                  }
                  });
                cargaListadoRecojos(); 

                /*guarda en local storage*/
                var listRecojoLS =JSON.stringify(obj_listado);
                var usernameLS = trim(result[0].ope_codigo);
                var passwordLS = trim(result[0].ope_codacc);
                localStorage.setItem('listRecojoLS', listRecojoLS);
                localStorage.setItem('usernameLS', usernameLS);
                localStorage.setItem('passwordLS', passwordLS);
               usuario_global=usernameLS;
               password_global=passwordLS;
               }else if(resultado==2){  /*error en credenciales o conexion*/   
                alert('Error al refrescar la lista de recojos')  
               }else if(resultado==3){/*no hay recojos pendientes*/
                /*localstorage*/
                cargaListadoRecojos();
                var listRecojoLS =JSON.stringify(obj_listado);
                var usernameLS = trim(result[0].ope_codigo);
                var passwordLS = trim(result[0].ope_codacc);
                localStorage.setItem('listRecojoLS', listRecojoLS);
                localStorage.setItem('usernameLS', usernameLS);
                localStorage.setItem('passwordLS', passwordLS);
               usuario_global=usernameLS;
               password_global=passwordLS;
               }
        }
    });

    }
   function cargaListadoRecojos(){/*se vale de la variable global que guarda la lista de recojos obj_listado */
    var cantRecojos=0;
    $("#recojosLista").html('')
      jQuery.each(obj_listado, function(i, obj){        
        $("#recojosLista").append('<li><a href="#" style="color:#000000; text-decoration:none;" class="smallList" style="white-space:normal; font-weight:bold;" onclick="linkrecojo('+parseInt(obj.nro_recojo)+');">'+obj.nro_recojo+' - '+obj.nom_cli+'</a></li>'); 
        cantRecojos++;
      }) 
     $("#txt_total_pendientes").html(cantRecojos);
         $("#recojosLista").listview();
         $("#recojosLista").listview('refresh');


   }
   function cargaListadoMotivos(){/*se vale de la variable global que guarda la lista de recojos obj_listado */
      jQuery.each(obj_motivos, function(i, obj){
        $("#motivos_opcion").append('<input type="radio" name="radio-choice" class="rbt_motivo" id="radio-'+i+'" value="'+obj.mot_codigo+'"/><label for="radio-'+i+'"  style="font-size:0.8em;">'+obj.mot_descripcion+'</label>');
      }) 

   }

   function getMotivosWebService(){
    $.ajax({
        url : 'http://www.olva.com.pe/WS_JSONP/cn/nOpeRecojos.php',
        jsonp: "callbackRecojos",
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
             var mot_codigo=obj.codigo;
             var mot_descripcion= obj.descripcion;

             obj_motivos[i]={'mot_codigo':mot_codigo, 
                              'mot_descripcion':mot_descripcion}             
            });
            cargaListadoMotivos();

                var listMotivoLS =JSON.stringify(obj_motivos);
                localStorage.setItem('listMotivoLS', listMotivoLS);
            }
        }
    });
   }


    function verificarSesion(){
      var usernameLS = localStorage.getItem('usernameLS');
      var passwordLS = localStorage.getItem('passwordLS');
      
      if(usernameLS=='' || passwordLS=='' || usernameLS==null || passwordLS==null ){
        logOut();
      }else{     
        recuperarSesion();
      }

    }


    function recuperarSesion(){
       console.log('Sesion Abierta')
        var usernameLS = localStorage.getItem('usernameLS');
        var passwordLS = localStorage.getItem('passwordLS');
        var listRecojoLS =localStorage.getItem('listRecojoLS');
        var listMotivoLS =localStorage.getItem('listMotivoLS');
        var listSolicPendientesLS =localStorage.getItem('listSolicPendientesLS');
        var objListRecojoLS=JSON.parse(listRecojoLS)
        var objlistMotivoLS=JSON.parse(listMotivoLS)
        var listSolicPendientesLS=JSON.parse(listSolicPendientesLS)
        /*lo guardamos en la variable global obj_listado y obj_motivos  e invocamos a la funcion 
        que carga la lista de recojos*/
        obj_listado=objListRecojoLS;
        obj_motivos=objlistMotivoLS;
        obj_solicPendientes=listSolicPendientesLS==null?new Array():listSolicPendientesLS;
        usuario_global=usernameLS;
        password_global=passwordLS;
        $.mobile.changePage( "#pageMenuPrincipal", { transition: "slidedown", changeHash: false });
        cargaListadoRecojos();
        cargaListadoMotivos();
    }

    function logOut(){
      console.log('No hay sesion')
      obj_listado='';
      obj_motivos='';
      usuario_global='';
      password_global='';
      obj_solicPendientes=new Array();

      /*BORRAR DATA EN LOCAL STORAGE*/
      window.localStorage.clear();
      $.mobile.changePage( "#pageLogin", { transition: "slidedown", changeHash: false });
      return false;

    }


 /*checkea cada cierto tiempo la conexion a internet y envia las solicitudes que hay pendientes*/
  setInterval(function(){
    var estadoConexion=app.checkConnection(); 
    if(estadoConexion!=false){/*hay conexion*/      
      var cantSolicitPend=obj_solicPendientes.length;
      if(cantSolicitPend>0){
        var obj_solicPendientesTmpLocal=obj_solicPendientes;
        obj_solicPendientes=new Array();/*inicializamos vacio la variable global que contiene la lista de pendientes*/
        localStorage.setItem('listSolicPendientesLS', JSON.stringify(obj_solicPendientes));/*inicial. la var. localstorage*/
        jQuery.each(obj_solicPendientesTmpLocal, function( i, obj ) {
          if(obj.funcion=='dMotivarRecojo'){
          alert('Se detecto conexion a internet, se motivara el recojo: '+obj.nro_recojo)  
            ejecutarConsultaMotivarRecojo(obj);
          }else if (obj.funcion=='dConfirmarRecojo'){
            alert('Se detecto conexion a internet, se confirmara el recojo:'+obj.nro_recojo)
              ejecutarConsultaConfirmarRecojo(obj)
          }
        })
      }
    }
  },60000*0.2);/*cada 30 minutos */
/*checkea la conexion a internet cada 15 minutos y si hay actualiza la lista de recojos*/
setInterval(function(){
    var estadoConexion=app.checkConnection(); 
    if(estadoConexion!=false){/*hay conexion*/ 
        $("#recojosLista").html('');   
                dRecojosListGet();   
    }
  },60000*0.8);/*cada 15 minutos */


});

      





 FUNCIONES
 ----------------------------
 
 
 var app = {
    // Application Constructor
    initialize: function() {
        this.bindEvents();
    },
    // Bind Event Listeners
    //
    // Bind any events that are required on startup. Common events are:
    // 'load', 'deviceready', 'offline', and 'online'.
    bindEvents: function() {
        document.addEventListener('deviceready', this.onDeviceReady, false);
    },
    // deviceready Event Handler
    //
    // The scope of 'this' is the event. In order to call the 'receivedEvent'
    // function, we must explicity call 'app.receivedEvent(...);'
    onDeviceReady: function() {
        app.receivedEvent('deviceready')
       // checkConnection();   

    },
    receivedEvent: function(id) {
        var parentElement = document.getElementById(id);
        var listeningElement = parentElement.querySelector('.listening');
        var receivedElement = parentElement.querySelector('.received');

        listeningElement.setAttribute('style', 'display:none;');
        receivedElement.setAttribute('style', 'display:block;');
        console.log('Received Event: ' + id);  
        var estadoConexion=app.checkConnection();


    },
    checkConnection: function () {/*HACE UN CHECK A LA CONEXION Y DEVUELVE*/
        var networkState = navigator.connection.type;

        var states = {};
        states[Connection.UNKNOWN]  = 'Unknown connection';
        states[Connection.ETHERNET] = 'Ethernet connection';
        states[Connection.WIFI]     = 'WiFi connection';
        states[Connection.CELL_2G]  = 'Cell 2G connection';
        states[Connection.CELL_3G]  = 'Cell 3G connection';
        states[Connection.CELL_4G]  = 'Cell 4G connection';
        states[Connection.CELL]     = 'Cell generic connection';
        states[Connection.NONE]     = 'No network connection';
        console.log(states[networkState])
        if(networkState == Connection.NONE){
            return false;
        }else{
            return states[networkState];            
        }

        }
};



APP.JS

-------------------------



body{
	font-size: 16px;
}
.alertHid{
	color:#752D2D;
	font-weight: bold;
}
#btnAddRmvDoc{
	display: block;
}
#lbl_operador{
	font-weight: bold;
}
#div_txt_emiOrden{
	padding:0 1em;
	width:35%;
}
#div_txt_numOrden{
	width:50%;
}
#div_btnAceptaConfirmar{
	width:70%;
	margin: 3em auto;	
}
.center{
	margin: 0 auto;	
}
.marcado{
	font-weight: bold;
}
#motivos_opcion{
	overflow: hidden;
}
#glosa_det{
	font-size: 1em;
}
.smallList{
	height:2em;
	font-size:0.7em;
}
.headerList{
	height: 1.3em;
}
.btnSmall{
	white-space:normal;
	font-size:0.7em;
}



ESTILOS .CSS










NO OLVIDAR, INSTALAR MEDIANTE CONSOLA DE COMANDOS DE CL EL PLUGIN PARA TENER ACCESO A LAS INFORMACION DE RED DEL MOVIL
LUEGO DE ESTO VERIFICAR EN EL ARCHIVO CONFIG.XML QUE EL PLUGIN ESTE AGREGADO























