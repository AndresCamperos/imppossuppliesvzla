<?xml version="1.0" encoding="utf-8"?>
<xsl:stylesheet version="1.0"
              	xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
              	xmlns:fo="http://www.w3.org/1999/XSL/Format"
              	xmlns:xs="http://www.w3.org/2001/XMLSchema"
              	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
              	xmlns:dgii="http://dgi-fep.mef.gob.pa"
              	xmlns:dgi="http://dgi-fep.mef.gob.pa"
              	xmlns:fox="http://xmlgraphics.apache.org/fop/extensions">
	<xsl:output method="xml"
          		indent="yes"/>
	<!-- Parámetros del constructor al XSL -->
	<xsl:param name="LogoBase64Image"/>
	<xsl:param name="EmisorRif"/>
	<xsl:param name="EmisorNombre"/>
	<xsl:param name="EmisorDomicilio"/>
	<xsl:param name="EmisorTelefono"/>
	<xsl:param name="EmisorCorreo"/>
	<xsl:param name="MarcaAguaPersonalizada"/>
	<xsl:param name="MarcaAgua"/>
	<xsl:param name="CodigoOperacion"/>
	<xsl:param name="PiePagImagen"/>
    <xsl:param name="EncabezadoImagen"/>
	<xsl:param name="MonedaBase"/>
	<xsl:param name="QrBase64Image"/>
	<!--Estilos-->
	<xsl:attribute-set name="BordeNN">
		<xsl:attribute name="border-top-style">none</xsl:attribute>
		<xsl:attribute name="border-top-width">0.18mm</xsl:attribute>
		<xsl:attribute name="border-top-color">#d9d9d9</xsl:attribute>
		<xsl:attribute name="border-left-style">none</xsl:attribute>
		<xsl:attribute name="border-left-width">0.18mm</xsl:attribute>
		<xsl:attribute name="border-left-color">#d9d9d9</xsl:attribute>
		<xsl:attribute name="border-right-style">none</xsl:attribute>
		<xsl:attribute name="border-right-width">0.18mm</xsl:attribute>
		<xsl:attribute name="border-right-color">#d9d9d9</xsl:attribute>
		<xsl:attribute name="border-bottom-style">none</xsl:attribute>
		<xsl:attribute name="border-bottom-width">0.18mm</xsl:attribute>
		<xsl:attribute name="border-bottom-color">#d9d9d9</xsl:attribute>
	</xsl:attribute-set>
	<xsl:attribute-set name="BorderEncabezado">
		<xsl:attribute name="border-top-style">solid</xsl:attribute>
		<xsl:attribute name="border-top-color">#ffffff</xsl:attribute>
		<xsl:attribute name="border-top-width">1</xsl:attribute>
	</xsl:attribute-set>
	<!-- Estilo de borde: Top -->
	<xsl:attribute-set name="BordeT">
		<xsl:attribute name="border-top-style">solid</xsl:attribute>
		<xsl:attribute name="border-top-width">1</xsl:attribute>
		<xsl:attribute name="border-top-color">#030F99</xsl:attribute>
	</xsl:attribute-set>
    <xsl:attribute-set name="BordeTR">
		<xsl:attribute name="border-top-style">solid</xsl:attribute>
		<xsl:attribute name="border-top-width">1.5</xsl:attribute>
		<xsl:attribute name="border-top-color">#D7D7D7</xsl:attribute>
	</xsl:attribute-set>
	<!-- Estilo de borde: Left -->
	<xsl:attribute-set name="BordeL">
		<xsl:attribute name="border-left-style">solid</xsl:attribute>
		<xsl:attribute name="border-left-width">2</xsl:attribute>
		<xsl:attribute name="border-left-color">#C0C0C0</xsl:attribute>
	</xsl:attribute-set>
	<!-- Estilo de borde: Right -->
	<xsl:attribute-set name="BordeR">
		<xsl:attribute name="border-right-style">solid</xsl:attribute>
		<xsl:attribute name="border-right-width">0.6</xsl:attribute>
		<xsl:attribute name="border-right-color">white</xsl:attribute>
	</xsl:attribute-set>
	<!-- Estilo de borde: Left -->
	<xsl:attribute-set name="BordeL2">
		<xsl:attribute name="border-left-style">solid</xsl:attribute>
		<xsl:attribute name="border-left-width">2</xsl:attribute>
		<xsl:attribute name="border-left-color">#000E32</xsl:attribute>
	</xsl:attribute-set>
	<!-- Estilo de borde: Right -->
	<xsl:attribute-set name="BordeR2">
		<xsl:attribute name="border-right-style">solid</xsl:attribute>
		<xsl:attribute name="border-right-width">1</xsl:attribute>
		<xsl:attribute name="border-right-color">white</xsl:attribute>
	</xsl:attribute-set>
	<!-- Estilo de borde: Right -->
	<xsl:attribute-set name="BordeR3">
		<xsl:attribute name="border-right-style">solid</xsl:attribute>
		<xsl:attribute name="border-right-width">1</xsl:attribute>
		<xsl:attribute name="border-right-color">#0C7BB2</xsl:attribute>
	</xsl:attribute-set>
	<!-- Estilo de borde: Bottom -->
	<xsl:attribute-set name="BordeB">
		<xsl:attribute name="border-bottom-style">solid</xsl:attribute>
		<xsl:attribute name="border-bottom-width">1</xsl:attribute>
		<xsl:attribute name="border-bottom-color">#A1A1A1</xsl:attribute>
	</xsl:attribute-set>
	<!-- Estilo de borde: Bottom AZUL-->
	<xsl:attribute-set name="BordeBA">
		<xsl:attribute name="border-bottom-style">solid</xsl:attribute>
		<xsl:attribute name="border-bottom-width">2</xsl:attribute>
		<xsl:attribute name="border-bottom-color">#0000F0</xsl:attribute>
	</xsl:attribute-set>
	<!-- Estilo de borde: Top AZUL-->
	<xsl:attribute-set name="BordeTA">
		<xsl:attribute name="border-top-style">solid</xsl:attribute>
		<xsl:attribute name="border-top-width">2</xsl:attribute>
		<xsl:attribute name="border-top-color">#0000F0</xsl:attribute>
	</xsl:attribute-set>

	<!-- Estilo de borde: All -->
	<xsl:attribute-set name="BordeAll">
		<xsl:attribute name="border-top-style">solid</xsl:attribute>
		<xsl:attribute name="border-top-width">1</xsl:attribute>
		<xsl:attribute name="border-top-color">#27347D</xsl:attribute>
		<xsl:attribute name="border-left-style">solid</xsl:attribute>
		<xsl:attribute name="border-left-width">1</xsl:attribute>
		<xsl:attribute name="border-left-color">#27347D</xsl:attribute>
		<xsl:attribute name="border-right-style">solid</xsl:attribute>
		<xsl:attribute name="border-right-width">1</xsl:attribute>
		<xsl:attribute name="border-right-color">#27347D</xsl:attribute>
		<xsl:attribute name="border-bottom-style">solid</xsl:attribute>
		<xsl:attribute name="border-bottom-width">1</xsl:attribute>
		<xsl:attribute name="border-bottom-color">#27347D</xsl:attribute>
	</xsl:attribute-set>
	<xsl:attribute-set name="BordeAllGris">
		<xsl:attribute name="border-top-style">solid</xsl:attribute>
		<xsl:attribute name="border-top-width">1</xsl:attribute>
		<xsl:attribute name="border-top-color">#D9D9D9</xsl:attribute>
		<xsl:attribute name="border-left-style">solid</xsl:attribute>
		<xsl:attribute name="border-left-width">0</xsl:attribute>
		<xsl:attribute name="border-left-color">#D9D9D9</xsl:attribute>
		<xsl:attribute name="border-right-style">solid</xsl:attribute>
		<xsl:attribute name="border-right-width">0</xsl:attribute>
		<xsl:attribute name="border-right-color">#D9D9D9</xsl:attribute>
		<xsl:attribute name="border-bottom-style">solid</xsl:attribute>
		<xsl:attribute name="border-bottom-width">1</xsl:attribute>
		<xsl:attribute name="border-bottom-color">#D9D9D9</xsl:attribute>
	</xsl:attribute-set>

	<xsl:attribute-set name="BordeTotales">
		<xsl:attribute name="border-top-style">solid</xsl:attribute>
		<xsl:attribute name="border-top-width">0.30mm</xsl:attribute>
		<xsl:attribute name="border-top-color">#1c1c1b</xsl:attribute>
		<xsl:attribute name="padding-top">0mm</xsl:attribute>
		<xsl:attribute name="border-left-style">solid</xsl:attribute>
		<xsl:attribute name="border-left-width">0.30mm</xsl:attribute>
		<xsl:attribute name="border-left-color">#1c1c1b</xsl:attribute>
		<xsl:attribute name="padding-left">0cm</xsl:attribute>
		<xsl:attribute name="border-right-style">solid</xsl:attribute>
		<xsl:attribute name="border-right-width">0.30mm</xsl:attribute>
		<xsl:attribute name="border-right-color">#1c1c1b</xsl:attribute>
		<xsl:attribute name="padding-right">1mm</xsl:attribute>
		<xsl:attribute name="border-bottom-style">solid</xsl:attribute>
		<xsl:attribute name="border-bottom-width">0.30mm</xsl:attribute>
		<xsl:attribute name="border-bottom-color">#1c1c1b</xsl:attribute>
		<xsl:attribute name="padding-bottom">0cm</xsl:attribute>
		<xsl:attribute name="background-color">#ececec</xsl:attribute>
	</xsl:attribute-set>
	<xsl:attribute-set name="Padding01">
		<xsl:attribute name="padding-top">1mm</xsl:attribute>
	</xsl:attribute-set>
	<!-- Estilo fuente título 01  -->
	<xsl:attribute-set name="Titulo01">
		<xsl:attribute name="font-size">12pt</xsl:attribute>
		<xsl:attribute name="font-family">Segoe UI Negrita</xsl:attribute> 
        <xsl:attribute name="color">#27347D</xsl:attribute>
		<!-- Tipo de letra descargar en formato .ttf y poner en proyecto carpeta/fonts-->
		<!-- <xsl:attribute name="color">#0000F0</xsl:attribute> -->
		<!--     <xsl:attribute name="padding-top">45pt</xsl:attribute> -->
	</xsl:attribute-set>
	<xsl:attribute-set name="Titulo02">
		<xsl:attribute name="font-size">11pt</xsl:attribute>
		<xsl:attribute name="font-family">Segoe UI Negrita</xsl:attribute>
		<xsl:attribute name="color">#FF0000</xsl:attribute>
		<xsl:attribute name="padding-top">0pt</xsl:attribute>
	</xsl:attribute-set>
	<xsl:attribute-set name="Titulo03">
		<xsl:attribute name="font-size">12pt</xsl:attribute>
		<xsl:attribute name="font-family">Segoe UI Negrita</xsl:attribute>
		<xsl:attribute name="color">#FF0000</xsl:attribute>
	</xsl:attribute-set>
    <xsl:attribute-set name="TituloN01">
		<xsl:attribute name="font-size">13pt</xsl:attribute>
		<xsl:attribute name="font-family">Segoe UI Negrita</xsl:attribute>
        <xsl:attribute name="font-weight">bold</xsl:attribute>
		<xsl:attribute name="color">#000000</xsl:attribute>
	</xsl:attribute-set>
    
	<xsl:attribute-set name="Texto01">
		<xsl:attribute name="font-size">9pt</xsl:attribute>
		<xsl:attribute name="font-family">Segoe UI Normal</xsl:attribute>
		<xsl:attribute name="color">black</xsl:attribute>
	</xsl:attribute-set>
	<xsl:attribute-set name="Texto02">
		<xsl:attribute name="font-size">8.25pt</xsl:attribute>
		<xsl:attribute name="font-family">Segoe UI Normal</xsl:attribute>
		<xsl:attribute name="color">black</xsl:attribute>
	</xsl:attribute-set>
	<xsl:attribute-set name="Texto03">
		<xsl:attribute name="font-size">6.8pt</xsl:attribute>
		<xsl:attribute name="font-family">Segoe UI Normal</xsl:attribute>
		<xsl:attribute name="color">black</xsl:attribute>
	</xsl:attribute-set>
	<xsl:attribute-set name="Texto04">
		<xsl:attribute name="font-size">6pt</xsl:attribute>
		<xsl:attribute name="font-family">Segoe UI Normal</xsl:attribute>
	</xsl:attribute-set>
	<xsl:attribute-set name="Texto05">
		<xsl:attribute name="font-size">12pt</xsl:attribute>
		<xsl:attribute name="font-family">Segoe UI Normal</xsl:attribute>
	</xsl:attribute-set>
     <xsl:attribute-set name="Texto075">
		<xsl:attribute name="font-size">7pt</xsl:attribute>
		<xsl:attribute name="font-family">Segoe UI Normal</xsl:attribute>
		<xsl:attribute name="color">#black</xsl:attribute>
	</xsl:attribute-set>
   <xsl:attribute-set name="ArialCursiva">
        <xsl:attribute name="font-size">10pt</xsl:attribute>
        <xsl:attribute name="font-family">Arial, Helvetica, sans-serif</xsl:attribute>
        <xsl:attribute name="font-style">italic</xsl:attribute>
        <xsl:attribute name="font-weight">normal</xsl:attribute>
        <xsl:attribute name="color">#5C5C5C</xsl:attribute>
    </xsl:attribute-set>
    <xsl:attribute-set name="LucidaSU">
        <xsl:attribute name="font-size">10pt</xsl:attribute>
        <xsl:attribute name="font-family">Lucida Sans Unicode, Segoe UI Normal</xsl:attribute>
        <xsl:attribute name="font-weight">normal</xsl:attribute>
        <xsl:attribute name="color">#37343C</xsl:attribute>
    </xsl:attribute-set>
    	<xsl:attribute-set name="TextoPieImprenta">
		<xsl:attribute name="font-size">7.2pt</xsl:attribute>
		<xsl:attribute name="color">#2E2E2D</xsl:attribute>
	</xsl:attribute-set>
    <xsl:attribute-set name="Texto08">
		<xsl:attribute name="font-size">8pt</xsl:attribute>
		<xsl:attribute name="font-family">Segoe UI Normal</xsl:attribute>
		<xsl:attribute name="color">#black</xsl:attribute>
	</xsl:attribute-set>
	
	<xsl:attribute-set name="TextoN01">
		<xsl:attribute name="font-size">9pt</xsl:attribute>
		<xsl:attribute name="font-family">Segoe UI Negrita</xsl:attribute>
		<xsl:attribute name="font-weight">bold</xsl:attribute>
		<xsl:attribute name="color">black</xsl:attribute>
	</xsl:attribute-set>
	<xsl:attribute-set name="TextoN02">
		<xsl:attribute name="font-size">8.25pt</xsl:attribute>
		<xsl:attribute name="font-family">Segoe UI Negrita</xsl:attribute>
		<xsl:attribute name="font-weight">bold</xsl:attribute>
		<xsl:attribute name="color">black</xsl:attribute>
	</xsl:attribute-set>
	<xsl:attribute-set name="TextoN03">
		<xsl:attribute name="font-size">6.8pt</xsl:attribute>
		<xsl:attribute name="font-family">Segoe UI Negrita</xsl:attribute>
		<xsl:attribute name="font-weight">bold</xsl:attribute>
		<xsl:attribute name="color">black</xsl:attribute>
	</xsl:attribute-set>
	<xsl:attribute-set name="TextoN04">
		<xsl:attribute name="font-size">6pt</xsl:attribute>
		<xsl:attribute name="font-family">Segoe UI Negrita</xsl:attribute>
		<xsl:attribute name="font-weight">bold</xsl:attribute>
		<xsl:attribute name="color">#101D7E</xsl:attribute>
	</xsl:attribute-set>
	<xsl:attribute-set name="TextoN05">
		<xsl:attribute name="font-size">12.5pt</xsl:attribute>
		<xsl:attribute name="font-family">Segoe UI Negrita</xsl:attribute>
		<xsl:attribute name="font-weight">bold</xsl:attribute>
	</xsl:attribute-set>
      <xsl:attribute-set name="TextoN075">
		<xsl:attribute name="font-size">7pt</xsl:attribute>
		<xsl:attribute name="font-family">Segoe UI Negrita</xsl:attribute>
        <xsl:attribute name="font-weight">bold</xsl:attribute>
		<xsl:attribute name="color">#black</xsl:attribute>
	</xsl:attribute-set>
    <xsl:attribute-set name="TextoN08">
		<xsl:attribute name="font-size">8pt</xsl:attribute>
		<xsl:attribute name="font-family">Segoe UI Negrita</xsl:attribute>
		<xsl:attribute name="font-weight">bold</xsl:attribute>
	</xsl:attribute-set>
	<xsl:attribute-set name="TextoN10">
		<xsl:attribute name="font-size">10pt</xsl:attribute>
		<xsl:attribute name="font-family">Segoe UI Negrita</xsl:attribute>
		<xsl:attribute name="font-weight">bold</xsl:attribute>
		<xsl:attribute name="color">#000000</xsl:attribute>
	</xsl:attribute-set>
	<xsl:attribute-set name="TextoN95">
		<xsl:attribute name="font-size">9pt</xsl:attribute>
		<xsl:attribute name="font-family">Segoe UI Negrita</xsl:attribute>
		<xsl:attribute name="font-weight">bold</xsl:attribute>
		<xsl:attribute name="color">#000000</xsl:attribute>
	</xsl:attribute-set>
	<xsl:attribute-set name="TextoN11">
		<xsl:attribute name="font-size">10.2pt</xsl:attribute>
		<xsl:attribute name="font-family">Segoe UI Negrita</xsl:attribute>
		<xsl:attribute name="font-weight">bold</xsl:attribute>
	</xsl:attribute-set>
	<!--Funciones-->
	<xsl:template name="IsZero">
		<xsl:param name="valor"/>
		<xsl:param name="decimales"/>
		<xsl:if test="$valor!=''">
			<xsl:choose>
				<xsl:when test="$decimales = '0'">
					<xsl:value-of select="$valor"/>
				</xsl:when>
				<xsl:otherwise>
					<xsl:choose>
						<xsl:when test="$valor > 1.00">
							<xsl:value-of select="format-number($valor, '###,###.00')"/>
						</xsl:when>
						<xsl:otherwise>
							<xsl:value-of select="format-number($valor,'0.00')"/>
						</xsl:otherwise>
					</xsl:choose>
				</xsl:otherwise>
			</xsl:choose>
		</xsl:if>
	</xsl:template>
	<xsl:template name="IsZero4Decimales">
		<xsl:param name="valor"/>
		<xsl:param name="decimales"/>
		<xsl:if test="$valor!=''">
			<xsl:choose>
				<xsl:when test="$decimales = '0'">
					<xsl:value-of select="$valor"/>
				</xsl:when>
				<xsl:otherwise>
					<xsl:choose>
						<xsl:when test="$valor > 1.00">
							<xsl:value-of select="format-number($valor, '###,###.0000')"/>
						</xsl:when>
						<xsl:otherwise>
							<xsl:value-of select="format-number($valor,'0.0000')"/>
						</xsl:otherwise>
					</xsl:choose>
				</xsl:otherwise>
			</xsl:choose>
		</xsl:if>
	</xsl:template>
	<xsl:template name="replace-br">
		<xsl:param name="text"
         			select="."/>
		<xsl:choose>
			<xsl:when test="not(contains($text, '&lt;br/>'))">
				<xsl:value-of select="$text"/>
			</xsl:when>
			<xsl:otherwise>
				<xsl:value-of select="substring-before($text, '&lt;br/>')"/>
				<!-- or <xsl:text>&#xA;</xsl:text>-->
				<fo:block xsl:use-attribute-sets="TextoN01">
					<xsl:call-template name="replace-br">
						<xsl:with-param name="text"
              							select="substring-after($text, '&lt;br/>')"/>
					</xsl:call-template>
				</fo:block>
			</xsl:otherwise>
		</xsl:choose>
	</xsl:template>
	<!-- _______________________ -->
	<xsl:template match="/" >
		<fo:root>
			<!-- Variables globales 
            <xsl:variable name="B10_FechaEmision" select="//dgii:Emisor/dgii:FechaEmision"/>-->
			<xsl:variable name="TipoDocumento"
            				select="//IdentificacionDocumento/TipoDocumento"/>
			<xsl:variable name="MonedaBase">
				<xsl:choose>
					<xsl:when test="//IdentificacionDocumento/Moneda='USD'">
						<xsl:value-of select="//IdentificacionDocumento/Moneda"/>	
					</xsl:when>	
					<xsl:otherwise>
						<xsl:value-of select="'Bs.'"/>
					</xsl:otherwise>
				</xsl:choose>
			</xsl:variable>					
			<!-- Formato principal tipo carta -->
			<fo:layout-master-set>
				<fo:simple-page-master master-name="carta-Vertical"
                     					page-height="28cm"
                     					page-width="21.6cm"
                                        margin-left="0.5cm"
									margin-right="0.5cm">
					<fo:region-body margin-top="9.6cm"
              						margin-bottom="1.9cm" /> 
					<fo:region-before extent=""/>
					<fo:region-after extent="1.9cm"/>
				</fo:simple-page-master>
			</fo:layout-master-set>
			<fo:page-sequence master-reference="carta-Vertical" >
				<!-- Encabezado -->
				<fo:static-content flow-name="xsl-region-before" >
                <fo:block-container absolute-position="absolute" 
										top="0cm" 
										left="0cm" 
										width="21.6cm" 
										height="28cm"
										background-image="url('data:image/png;base64,{$MarcaAguaPersonalizada}')" 
										background-repeat="no-repeat" 
										background-position-horizontal="5.6cm" 
										background-position-vertical="6.1cm" 
										fox:background-image-height="9.8cm">
						<fo:block/>
					</fo:block-container>			
					<fo:block  xsl:use-attribute-sets="">					
						<!-- Tabla para el encabezado 20    background-image="url('data:image/png;base64,{$MarcaAgua}')"-->
						<fo:table table-layout="fixed"									
        							width="100%"
									
        							background-repeat="repeat"
        							background-position-horizontal="center"
        							background-position-vertical="center">
							<fo:table-column column-width="100%" />
							<fo:table-body>
								<fo:table-row>	  
									<fo:table-cell xsl:use-attribute-sets="">
										<fo:block background-color="">
                                            <fo:table table-layout="fixed" width="100%">
                                                <fo:table-column column-width="65%"/>
                                                <fo:table-column column-width="35%"/>
                                                <fo:table-body>
                                                    <fo:table-row>
                                                        <fo:table-cell display-align="center" >
                                                            <fo:block text-align="left">
                                                                <fo:table table-layout="fixed" width="100%">
                                                                    <fo:table-column column-width="30%"/>
                                                                    <fo:table-column column-width="70%"/>
                                                                    <fo:table-body>
                                                                        <fo:table-row>
                                                                            <fo:table-cell padding-top="3mm" display-align="center" xsl:use-attribute-sets="" margin-left="0cm">
                                                                                <fo:block text-align="left">
                                                                                    <fo:external-graphic content-width="100%"
                                                                                    vertical-align="middle"																 																 
                                                                                    scaling="uniform"
                                                                                    src="url('data:image/png;base64,{$LogoBase64Image}')" />
                                                                                </fo:block>
                                                                            </fo:table-cell>
                                                                            <fo:table-cell display-align="center" xsl:use-attribute-sets="">
                                                                                <fo:block>
                                                                                    <fo:table table-layout="fixed" xsl:use-attribute-sets=""
                                                                                                width="100%" >
                                                                                        <fo:table-column column-width="100%"/>
                                                                                        <fo:table-body>
                                                                                            <fo:table-row>
                                                                                                <fo:table-cell xsl:use-attribute-sets="TituloN01" padding-top="0mm" padding-right="0mm" margin-left="0cm" padding-left="0mm">
                                                                                                    <fo:block text-align="left">
                                                                                                        IMPORTADORA POS SUPPLIES DE
                                                                                                    </fo:block>
                                                                                                </fo:table-cell>
                                                                                            </fo:table-row>
                                                                                            <fo:table-row>
                                                                                                <fo:table-cell xsl:use-attribute-sets="TituloN01" padding-top="0mm" padding-right="0mm" margin-left="0cm" padding-left="0mm">
                                                                                                    <fo:block text-align="left" color="black">
                                                                                                        VENEZUELA, CA - Grupo Lebomar
                                                                                                    </fo:block>
                                                                                                </fo:table-cell>
                                                                                            </fo:table-row>
                                                                                            <fo:table-row>
                                                                                                <fo:table-cell xsl:use-attribute-sets="TextoN01" padding-top="0mm" padding-right="0mm" padding-bottom="0mm" padding-left="0mm" margin-left="0cm">
                                                                                                    <fo:block text-align="left" color="">
                                                                                                        RIF:&#160;<xsl:value-of select="substring($EmisorRif, 1, string-length($EmisorRif) - 1)" />-<xsl:value-of select="substring($EmisorRif, string-length($EmisorRif), 1)" />
                                                                                                    </fo:block>
                                                                                                </fo:table-cell>
                                                                                            </fo:table-row>
                                                                                            <fo:table-row>
                                                                                                <fo:table-cell xsl:use-attribute-sets="TextoN01" padding-top="0mm" padding-right="0mm" padding-bottom="0mm" padding-left="0mm" margin-left="0cm">
                                                                                                    <fo:block text-align="left">
                                                                                                        Cod. Operación:&#160;<fo:inline xsl:use-attribute-sets="Texto02"><xsl:value-of select="$CodigoOperacion"/></fo:inline>
                                                                                                    </fo:block>      
                                                                                                </fo:table-cell>  
                                                                                            </fo:table-row>
                                                                                        </fo:table-body>
                                                                                    </fo:table>
                                                                                </fo:block>
                                                                            </fo:table-cell>
                                                                        </fo:table-row>
                                                                        <fo:table-row xsl:use-attribute-sets="LucidaSU">
                                                                            <fo:table-cell number-columns-spanned="2" padding-left="2mm" padding-top="2mm">
                                                                                <fo:block>
                                                                                    Calle Los Laboratorios, Edf. Torre Beta, Piso 4 Ofc 401, Urb. 
                                                                                </fo:block>
                                                                            </fo:table-cell>
                                                                        </fo:table-row>
                                                                         <fo:table-row xsl:use-attribute-sets="LucidaSU" >
                                                                            <fo:table-cell number-columns-spanned="2" padding-left="2mm">
                                                                                <fo:block>
                                                                                    Los Ruices, Caracas, Miranda - Zona Postal 1071 
                                                                                </fo:block>
                                                                            </fo:table-cell>
                                                                        </fo:table-row>
                                                                         <fo:table-row xsl:use-attribute-sets="LucidaSU" >
                                                                            <fo:table-cell number-columns-spanned="2" padding-left="2mm">
                                                                                <fo:block>
                                                                                    Telfs.: (0212) 239 48 18 - 238 60 08
                                                                                </fo:block>
                                                                            </fo:table-cell>
                                                                        </fo:table-row>
                                                                         <fo:table-row xsl:use-attribute-sets="LucidaSU" >
                                                                            <fo:table-cell number-columns-spanned="2" padding-left="2mm">
                                                                                <fo:block>
                                                                                    Cel. : (0414) 121 18 67 
                                                                                </fo:block>
                                                                            </fo:table-cell>
                                                                        </fo:table-row>
                                                                         <fo:table-row xsl:use-attribute-sets="LucidaSU">
                                                                            <fo:table-cell number-columns-spanned="2" padding-left="2mm">
                                                                                <fo:block>
                                                                                    email: info@lebomarvzla.com / www.lebomarvzla.com
                                                                                </fo:block>
                                                                            </fo:table-cell>
                                                                        </fo:table-row>
                                                                    </fo:table-body>
                                                                </fo:table>	
                                                            </fo:block>
                                                        </fo:table-cell>
                                                        <fo:table-cell display-align="center" xsl:use-attribute-sets="">
                                                            <fo:block text-align="left">
                                                                <fo:table table-layout="fixed"
																			width="100%" >
																	<fo:table-column column-width="100%"/>
																	<fo:table-body>
																		<fo:table-row>
																			<fo:table-cell display-align="center">
																				<fo:block>
																					<fo:table table-layout="fixed"
																							width="100%" >
																						<fo:table-column column-width="100%"/>
																						<fo:table-body>
																							<fo:table-row>
																								<xsl:choose>
																									<xsl:when test="//Anulacion != ''">
																										<fo:table-cell height="0.6cm" xsl:use-attribute-sets="Titulo01" padding-left="-0.5mm" padding-bottom="0mm" padding-top="0mm" display-align="center">
																											<fo:block text-align="left" color="#6CB4D4" >
																												<xsl:choose>
																													<xsl:when test="$TipoDocumento = 1">FACTURA <fo:inline color="#D3392D"> ANULADA</fo:inline></xsl:when>
																													<xsl:when test="$TipoDocumento = 2">NOTA DE CRÉDITO <fo:inline color="#D3392D"> ANULADA</fo:inline></xsl:when>
																													<xsl:when test="$TipoDocumento = 3">NOTA DE DÉBITO <fo:inline color="#D3392D"> ANULADA</fo:inline></xsl:when>
																													<xsl:when test="$TipoDocumento = 4">GUÍA DE DESPACHO <fo:inline color="#D3392D"> ANULADA</fo:inline></xsl:when>
																												</xsl:choose>
																											</fo:block>
																										</fo:table-cell>
																									</xsl:when>	
																									<xsl:otherwise>
																										<fo:table-cell height="0.6cm" xsl:use-attribute-sets="Titulo01" padding-left="-0.5mm" padding-bottom="0mm" padding-top="0mm" display-align="center">
																											<fo:block text-align="left" color="#6CB4D4" background-color="" >
																												<xsl:choose>
																													<xsl:when test="$TipoDocumento = 1">FACTURA</xsl:when>
																													<xsl:when test="$TipoDocumento = 2">NOTA DE CRÉDITO</xsl:when>
																													<xsl:when test="$TipoDocumento = 3">NOTA DE DÉBITO</xsl:when>
																													<xsl:when test="$TipoDocumento = 4">GUÍA DE DESPACHO</xsl:when>
																												</xsl:choose>
																											</fo:block>
																										</fo:table-cell>
																									</xsl:otherwise>
																								</xsl:choose>		
																							</fo:table-row>
																						</fo:table-body>
																					</fo:table>
																				</fo:block>
																			</fo:table-cell>
																		</fo:table-row>
																		<fo:table-row>
                                                                            <fo:table-cell>
                                                                                <fo:block>
                                                                                    <fo:table table-layout="fixed" width="100%">
                                                                                        <fo:table-column column-width="100%"/>
                                                                                        <fo:table-body>
                                                                                            <fo:table-row>
                                                                                                <fo:table-cell display-align="center" >
                                                                                                    <fo:block border-style="solid"
                                                                                                            border-width="1"
                                                                                                            fox:border-radius="13"
                                                                                                            text-align="center"
                                                                                                            background-color="#D7D7D7"
                                                                                                            border-top-color="#D7D7D7"
                                                                                                            border-bottom-color="#D7D7D7"
                                                                                                            border-left-color="#D7D7D7"
                                                                                                            border-right-color="#D7D7D7">
                                                                                                        <fo:table table-layout="fixed" width="100%">
                                                                                                            <fo:table-column column-width="60%"/>
                                                                                                            <fo:table-column column-width="40%"/>
                                                                                                            <fo:table-body>
                                                                                                                <fo:table-row>
                                                                                                                    <fo:table-cell padding-top="2mm" padding-left="3mm" display-align="center" xsl:use-attribute-sets="ArialCursiva">
                                                                                                                        <fo:block text-align="left" >
                                                                                                                            N° De Documento:
                                                                                                                        </fo:block>      
                                                                                                                    </fo:table-cell>
                                                                                                                    <fo:table-cell padding-top="2mm" padding-right="2mm" padding-left="1.5mm" display-align="center" xsl:use-attribute-sets="Texto01">
                                                                                                                        <fo:block text-align="right" color="#5C5C5C">
                                                                                                                            <fo:inline xsl:use-attribute-sets="Texto02" color=""><xsl:value-of select="format-number(//IdentificacionDocumento/NumeroDocumento,'00000000')"/></fo:inline> 
                                                                                                                        </fo:block>      
                                                                                                                    </fo:table-cell>   
                                                                                                                </fo:table-row> 
                                                                                                                <fo:table-row>   
                                                                                                                    <fo:table-cell padding-top="2mm"  padding-left="3mm" display-align="center" xsl:use-attribute-sets="ArialCursiva">
                                                                                                                        <fo:block text-align="left">
                                                                                                                            Fecha de Emisión:
                                                                                                                        </fo:block>      
                                                                                                                    </fo:table-cell>
                                                                                                                    <fo:table-cell padding-top="2mm" padding-right="2mm" padding-left="1.5mm" display-align="center" xsl:use-attribute-sets="Texto01">
                                                                                                                        <fo:block text-align="right">
                                                                                                                            <fo:inline xsl:use-attribute-sets="Texto02" color="#5C5C5C"><xsl:value-of select="translate(//Encabezado/IdentificacionDocumento/FechaEmision, '/','-')"/></fo:inline>
                                                                                                                        </fo:block>      
                                                                                                                    </fo:table-cell>      
                                                                                                                </fo:table-row> 
                                                                                                                <fo:table-row>   
                                                                                                                    <fo:table-cell padding-top="2mm"  padding-left="3mm" display-align="center" xsl:use-attribute-sets="ArialCursiva">
                                                                                                                        <fo:block text-align="left">
                                                                                                                            Hora de Emisión:
                                                                                                                        </fo:block>      
                                                                                                                    </fo:table-cell>
                                                                                                                    <fo:table-cell padding-top="2mm" padding-right="2mm" padding-left="1.5mm" display-align="center" xsl:use-attribute-sets="Texto01">
                                                                                                                        <fo:block text-align="right" color="#5C5C5C">
                                                                                                                            <fo:inline xsl:use-attribute-sets="Texto02" color="#5C5C5C"><xsl:value-of select="//Encabezado/IdentificacionDocumento/HoraEmision"/></fo:inline>
                                                                                                                        </fo:block>      
                                                                                                                    </fo:table-cell>    
                                                                                                                </fo:table-row>
                                                                                                                <fo:table-row>   
                                                                                                                    <fo:table-cell padding-top="2mm"  padding-left="3mm" display-align="center" xsl:use-attribute-sets="ArialCursiva">
                                                                                                                        <fo:block text-align="left">
                                                                                                                            N° de Control:
                                                                                                                        </fo:block>      
                                                                                                                    </fo:table-cell>
                                                                                                                    <fo:table-cell padding-top="2mm" padding-right="2mm" padding-left="1.5mm" display-align="center" xsl:use-attribute-sets="Texto01">
                                                                                                                        <fo:block text-align="right" color="#5C5C5C">
                                                                                                                            <fo:inline xsl:use-attribute-sets="TextoN02" color="red"><xsl:value-of select="//Imprenta/NumeroControl"/></fo:inline>
                                                                                                                        </fo:block>      
                                                                                                                    </fo:table-cell>  
                                                                                                                </fo:table-row>
                                                                                                                <fo:table-row>   
                                                                                                                    <fo:table-cell padding-top="2mm"  padding-left="3mm" display-align="center" xsl:use-attribute-sets="ArialCursiva">
                                                                                                                        <fo:block text-align="left">
                                                                                                                            Fecha de Asignación:
                                                                                                                        </fo:block>      
                                                                                                                    </fo:table-cell>
                                                                                                                    <fo:table-cell padding-top="2mm" padding-right="2mm" padding-left="1.5mm" display-align="center" xsl:use-attribute-sets="TextoN02">
                                                                                                                        <fo:block text-align="right" color="#5C5C5C">
                                                                                                                            <fo:inline xsl:use-attribute-sets="Texto02" color="#5C5C5C"><xsl:value-of select="translate(//Imprenta/FechaAsignacionNumeroControl, '/','-')"/></fo:inline>
                                                                                                                        </fo:block>      
                                                                                                                    </fo:table-cell>    
                                                                                                                </fo:table-row>
                                                                                                                <fo:table-row>   
                                                                                                                    <fo:table-cell padding-top="2mm"  padding-left="3mm"  padding-bottom="2mm" display-align="center" xsl:use-attribute-sets="ArialCursiva">
                                                                                                                        <fo:block text-align="left">
                                                                                                                            Fecha de Vencimiento:
                                                                                                                        </fo:block>      
                                                                                                                    </fo:table-cell>
                                                                                                                    <fo:table-cell padding-top="2mm" padding-right="2mm" padding-bottom="2mm" padding-left="1.5mm" display-align="center" xsl:use-attribute-sets="TextoN02">
                                                                                                                        <fo:block text-align="right" color="#5C5C5C">
                                                                                                                            <fo:inline xsl:use-attribute-sets="Texto02" color="#5C5C5C"><xsl:value-of select="translate(//Encabezado/IdentificacionDocumento/FechaVencimiento, '/','-')"/></fo:inline>
                                                                                                                        </fo:block>      
                                                                                                                    </fo:table-cell>    
                                                                                                                </fo:table-row>
                                                                                                            </fo:table-body>
                                                                                                        </fo:table>
                                                                                                    </fo:block>
                                                                                                </fo:table-cell>
                                                                                            </fo:table-row>
                                                                                        </fo:table-body>
                                                                                    </fo:table>
                                                                                </fo:block>
                                                                            </fo:table-cell>
																		</fo:table-row>
																	</fo:table-body>
																</fo:table>
                                                            </fo:block>
                                                        </fo:table-cell>
                                                    </fo:table-row>
                                                </fo:table-body>
                                            </fo:table>
										</fo:block>
									</fo:table-cell>				
								</fo:table-row>	
                                <fo:table-row>
                                    <fo:table-cell height="0.2cm">
                                        <fo:block></fo:block>
                                    </fo:table-cell>
                                </fo:table-row>
                                <fo:table-row>
									<fo:table-cell padding-top="0mm" height=""  xsl:use-attribute-sets="">
										<fo:block border-style="solid"
												border-width="0"
												fox:border-radius="" 
												text-align="center"
												background-color="#6CB4D4"
												border-top-color="#6CB4D4"
												border-bottom-color="#6CB4D4"
												border-left-color="#6CB4D4"
												border-right-color="#6CB4D4">
											<fo:table table-layout="fixed"
														width="100%"
														xsl:use-attribute-sets="">
                                                <fo:table-column column-width="100%"/>
														
												<fo:table-body>												
													<fo:table-row>
                                                        <fo:table-cell height="" xsl:use-attribute-sets="ArialCursiva" display-align="center" padding-top="1mm"  padding-bottom="1mm" padding-left="2mm">
															<fo:block text-align="left" color="white" font-weight="bold">
																Datos del cliente:
															</fo:block>
														</fo:table-cell>							
													</fo:table-row>
                                                    										
												</fo:table-body>
											</fo:table>		
										</fo:block>
									</fo:table-cell>
								</fo:table-row>
                                <fo:table-row>
									<fo:table-cell number-columns-spanned="">
										<fo:block-container overflow="hidden" height="3cm">
                                            <fo:block margin-left="1mm">
                                                    <fo:table table-layout="fixed" xsl:use-attribute-sets=""
                                                            width="100%" >
                                                    <fo:table-column column-width="65%"/>
                                                    <fo:table-column column-width="35%"/>
                                                    <fo:table-body>
                                                        <fo:table-row>
                                                            <fo:table-cell display-align="center" xsl:use-attribute-sets="TextoN02 " padding-left="" padding-top="2mm" padding-right="0mm">
                                                                <fo:block>
                                                                    Nombre o Razón Social:&#160;<fo:inline xsl:use-attribute-sets="Texto02"><xsl:value-of select="//Comprador/RazonSocial"/></fo:inline>
                                                                </fo:block>
                                                            </fo:table-cell>
                                                            <fo:table-cell display-align="center" xsl:use-attribute-sets="TextoN02" padding-left="" padding-bottom="0mm" padding-top="2mm" padding-right="0mm">
                                                                <fo:block text-align="left" >
                                                                    Correo:&#160;<fo:inline xsl:use-attribute-sets="Texto02"><xsl:value-of select="//Comprador/Correo/CorreoComprador1"/></fo:inline>
                                                                </fo:block>	
                                                            </fo:table-cell>
                                                        </fo:table-row>
                                                        <fo:table-row>
                                                            <fo:table-cell display-align="center" xsl:use-attribute-sets="TextoN02 " padding-left="" padding-bottom="0mm" padding-top="2mm" padding-right="0mm" >
                                                                <fo:block text-align="left" >
                                                                    Domicilio Fiscal:&#160;<fo:inline xsl:use-attribute-sets="Texto02"><xsl:value-of select="//Comprador/Direccion"/></fo:inline>
                                                                </fo:block>	  
                                                            </fo:table-cell>
                                                            <fo:table-cell display-align="center" xsl:use-attribute-sets="TextoN02 " padding-left="" padding-bottom="0mm" padding-top="2mm" padding-right="0mm" >
                                                                <fo:block text-align="left" >
                                                                    Condición:&#160;<fo:inline xsl:use-attribute-sets="Texto02"><xsl:value-of select="//IdentificacionDocumento/TipoDePago"/></fo:inline>
                                                                </fo:block>	  
                                                            </fo:table-cell>
                                                        </fo:table-row>
                                                        <fo:table-row>
                                                            <fo:table-cell display-align="center" xsl:use-attribute-sets="TextoN02 " padding-left="" padding-bottom="0mm" padding-top="2mm" padding-right="0mm">
                                                                <fo:block text-align="left">
                                                                    RIF o C.I.:&#160;<fo:inline xsl:use-attribute-sets="Texto02"><xsl:value-of select="//Comprador/TipoIdentificacion"/>-<xsl:value-of select="//Comprador/NumeroIdentificacion"/></fo:inline>
                                                                </fo:block>
                                                            </fo:table-cell>
                                                            <fo:table-cell>
                                                                <fo:block>
                                                                </fo:block>
                                                            </fo:table-cell>
                                                        </fo:table-row>
                                                        <fo:table-row>
                                                            <fo:table-cell display-align="center" xsl:use-attribute-sets="TextoN02 " padding-left="" padding-bottom="0mm" padding-top="2mm" padding-right="0mm">
                                                                <fo:block text-align="left" >
                                                                    Teléfono:&#160;<fo:inline xsl:use-attribute-sets="Texto02"><xsl:value-of select="//Comprador/Telefono/TelefonoComprador1"/></fo:inline>
                                                                </fo:block>	
                                                            </fo:table-cell>
                                                            <fo:table-cell display-align="center" xsl:use-attribute-sets="TextoN02 " padding-left="" padding-bottom="0mm" padding-top="2mm" padding-right="0mm">
                                                                <fo:block>
                                                                    Vendedor:&#160;<fo:inline xsl:use-attribute-sets="Texto02"><xsl:value-of select="//Vendedor/Nombre"/></fo:inline>
                                                                </fo:block>
                                                            </fo:table-cell>
                                                        </fo:table-row>
                                                        
                                                    </fo:table-body>
                                                </fo:table>
                                            </fo:block>
                                        </fo:block-container>
									</fo:table-cell>
								</fo:table-row>
								<fo:table-row>
									<fo:table-cell padding-top="0mm" height=""  xsl:use-attribute-sets="">
										<fo:block border-style="solid"
												border-width="0"
												fox:border-radius="" 
												text-align="center"
												background-color="#6CB4D4"
												border-top-color="#6CB4D4"
												border-bottom-color="#6CB4D4"
												border-left-color="#6CB4D4"
												border-right-color="#6CB4D4">
											<fo:table table-layout="fixed"
														width="100%"
														xsl:use-attribute-sets="">
                                                        <fo:table-column column-width="8%"/>
														<fo:table-column column-width="39%"/>
                                                        <fo:table-column column-width="8%"/>
                                                        <fo:table-column column-width="15%"/>
														<fo:table-column column-width="15%"/>
														<fo:table-column column-width="15%"/>
												<fo:table-body>												
													<fo:table-row>
                                                        <fo:table-cell height="0.5cm" xsl:use-attribute-sets="ArialCursiva BordeR2" display-align="center" padding-top="1mm"  padding-bottom="0.5mm" margin-left="0cm" margin-right="0cm">
															<fo:block text-align="center" color="white" font-weight="bold">
																Código
															</fo:block>
														</fo:table-cell>	
														<fo:table-cell height="0.5cm" xsl:use-attribute-sets="ArialCursiva BordeR2" display-align="center" padding-top="1mm"  padding-bottom="0.5mm" margin-left="0.5cm" margin-right="0cm">
															<fo:block text-align="center" color="white" font-weight="bold">
																Descripción / Producto
															</fo:block>
														</fo:table-cell>
                                                        <fo:table-cell height="0.5cm" xsl:use-attribute-sets="ArialCursiva BordeR2" display-align="center" padding-top="1mm"  padding-bottom="0.5mm" margin-left="0cm" margin-right="0cm">
															<fo:block text-align="center" color="white" font-weight="bold">
																Cant
															</fo:block>
														</fo:table-cell>
														<fo:table-cell height="0.5cm" xsl:use-attribute-sets="ArialCursiva BordeR2" display-align="center" padding-top="1mm"  padding-bottom="0.5mm" margin-left="0cm" margin-right="0cm">
															<fo:block text-align="center" color="white" font-weight="bold">
																P Unitario
															</fo:block>
														</fo:table-cell>
                                                        <fo:table-cell height="0.5cm" xsl:use-attribute-sets="ArialCursiva BordeR2" display-align="center" padding-top="1mm"  padding-bottom="0.5mm" margin-left="0cm" margin-right="0cm">
															<fo:block text-align="center" color="white" font-weight="bold">
																Alícuota I.V.A.
															</fo:block>
														</fo:table-cell>
														<fo:table-cell height="0.5cm" xsl:use-attribute-sets="ArialCursiva" display-align="center" padding-top="1mm" padding-bottom="0.5mm" padding-right="" padding-left="0mm" margin-left="0cm" margin-right="0cm">
															<fo:block text-align="center" color="white" font-weight="bold">
																Total
															</fo:block>
														</fo:table-cell>													
													</fo:table-row>												
												</fo:table-body>
											</fo:table>		
										</fo:block>
									</fo:table-cell>
								</fo:table-row>
							</fo:table-body>
						</fo:table>
					</fo:block>
				</fo:static-content>
				<!-- Pie de página -->
				<fo:static-content flow-name="xsl-region-after">
					<fo:block background-image="">
						<fo:table table-layout="fixed"
									width="100%">
							<fo:table-column column-width="100%"/>
							<fo:table-body>						
								<fo:table-row>
									<fo:table-cell margin-left="" margin-right="" xsl:use-attribute-sets="" background-color=""  height="" display-align="center" padding-top="-0.5mm">
										<fo:block border-style=""
												border-width=""
												fox:border-radius="" 
												text-align="center"
												background-color=""
												border-top-color=""
												border-bottom-color=""
												border-left-color=""
												border-right-color="">
											<fo:table table-layout="fixed"
														width="100%">
												
                                                <fo:table-column column-width="100%"/>
												<fo:table-body>
                                                    <fo:table-row>
                                                        <fo:table-cell height="2mm" background-color="#6CB4D4" number-columns-spanned="">
                                                            <fo:block></fo:block>
                                                        </fo:table-cell>
                                                    </fo:table-row>
                                                    <fo:table-row>
                                                        <fo:table-cell  number-columns-spanned="" padding-left="2mm" display-align="center" padding-top="1mm" margin-right="0cm" margin-left="0cm">
                                                            <fo:block >
                                                                <fo:table table-layout="fixed" width="100%">
                                                                    <fo:table-body>
                                                                        <!-- No modificar **************************************************** -->
                                                                        <fo:table-row xsl:use-attribute-sets="TextoPieImprenta" font-weight="bold">
                                                                            <fo:table-cell padding-top="1mm">
                                                                                <fo:block text-align="center">
                                                                                    <xsl:value-of select="//Imprenta/Snat"/>
                                                                                </fo:block>
                                                                            </fo:table-cell>
                                                                        </fo:table-row>
                                                                        
                                                                        <fo:table-row xsl:use-attribute-sets="TextoPieImprenta">
                                                                            <fo:table-cell padding-top="1.5mm"
                                                                                            xsl:use-attribute-sets="" >
                                                                                <fo:block text-align="center">
                                                                                    <xsl:value-of select="//Imprenta/Nombre"/>&#160;<xsl:value-of select="//Imprenta/RIF"/>,&#160;<xsl:value-of select="//Imprenta/Direccion"/>&#160;<xsl:value-of select="//Imprenta/Telefonos"/>.&#160; <xsl:value-of select="//Imprenta/Autorizacion"/>
                                                                                    Nros de Control desde el N° <xsl:value-of select="//Imprenta/RangoInicial"/> hasta el N° <xsl:value-of select="//Imprenta/RangoFinal"/> generados digitalmente en 
                                                                                    fecha <xsl:value-of select="//Imprenta/FechaAsignacion"/>.
                                                                                </fo:block>
                                                                            </fo:table-cell>
                                                                        </fo:table-row>
                                                                        <!-- ***************************************************************** -->
                                                                    </fo:table-body>
                                                                </fo:table>
                                                            </fo:block >
                                                        </fo:table-cell>
                                                    </fo:table-row>
                                                </fo:table-body>
											</fo:table>	
										</fo:block>
									</fo:table-cell>
								</fo:table-row>
							</fo:table-body>
						</fo:table>
					</fo:block>
				</fo:static-content>
				<!-- Contenido -->
				<fo:flow flow-name="xsl-region-body">
					<fo:block>
						<fo:block xsl:use-attribute-sets="" margin-left="" margin-right="">
							<fo:table table-layout="fixed" width="100%">
								<fo:table-column column-width="8%"/>
                                <fo:table-column column-width="39%"/>
                                <fo:table-column column-width="8%"/>
                                <fo:table-column column-width="15%"/>
                                <fo:table-column column-width="15%"/>
                                <fo:table-column column-width="15%"/>
								<fo:table-body>
									<xsl:for-each select="//Item">
                                        <fo:table-row xsl:use-attribute-sets="Texto02" >
                                             <fo:table-cell height="3mm" background-color="" padding-top="0.5mm" padding-bottom="0mm" display-align="center" xsl:use-attribute-sets=""
                                                            padding-left="" padding-right="" margin-left="0cm" margin-right="0cm">
                                                <fo:block text-align="center">
                                                    <xsl:value-of select="CodigoPLU"/>
                                                </fo:block>
                                            </fo:table-cell>
                                            <fo:table-cell  background-color="" padding-top="0.5mm" padding-bottom="0mm" display-align="center" xsl:use-attribute-sets=""
                                                            padding-left="0mm" padding-right="" margin-left="0cm" margin-right="0cm">
                                                <fo:block text-align="left">
                                                    <xsl:value-of select="Descripcion"/>
                                                </fo:block>
                                            </fo:table-cell>
                                            <fo:table-cell background-color="" padding-top="0.5mm" padding-bottom="0mm" display-align="center" xsl:use-attribute-sets=""
                                                            padding-left="" padding-right="" margin-left="0cm" margin-right="0cm">
                                                <fo:block text-align="center">
                                                    <xsl:value-of select="Cantidad"/>
                                                </fo:block>
                                            </fo:table-cell>
                                            
                                            <fo:table-cell background-color="" padding-top="0.5mm" padding-bottom="0mm" display-align="center" xsl:use-attribute-sets=""
                                                            padding-right="" margin-left="0cm" margin-right="0cm">
                                                <fo:block text-align="right">
                                                   <xsl:value-of select="$MonedaBase"/>&#160;<xsl:call-template name="IsZero">
                                                        <xsl:with-param name="valor"
                                                                        select="PrecioUnitario"/>
                                                        <xsl:with-param name="decimales"
                                                                        select="2"/>
                                                    </xsl:call-template>
                                                </fo:block>
                                            </fo:table-cell>
                                            <fo:table-cell background-color="" padding-top="0.5mm" padding-bottom="0mm" display-align="center" xsl:use-attribute-sets=""
                                                            padding-right="" margin-left="0cm" margin-right="0cm">
																<fo:block text-align="center">
																	(<xsl:value-of select="CodigoImpuesto"/>)
																</fo:block>
															</fo:table-cell>	
                                            <fo:table-cell background-color="" padding-top="0.5mm" padding-bottom="0mm" display-align="center" xsl:use-attribute-sets=""
                                                            padding-right="0.25mm" margin-left="0cm" margin-right="0cm">
                                                <fo:block text-align="right">
                                                    <xsl:value-of select="$MonedaBase"/>&#160;<xsl:call-template name="IsZero">
                                                        <xsl:with-param name="valor"
                                                                        select="PrecioItem"/>
                                                        <xsl:with-param name="decimales"
                                                                        select="2"/>
                                                    </xsl:call-template>
                                                </fo:block>
                                            </fo:table-cell>					
                                        </fo:table-row>				
									</xsl:for-each>	
								</fo:table-body>
							</fo:table>
						</fo:block>							
						
						<!-- Table totales-->
						<fo:block keep-with-previous.within-page="always"
        							keep-together.within-page="always"
        							space-before.minimum="0.1cm"
        							space-before.optimum="30cm"
        							space-before.maximum="30cm"
        							border-style=""
        							border-width=""
        							fox:border-radius=""
									margin-top=""
									margin-left=""
									margin-right="0mm">
							<fo:table table-layout="fixed"
								width="100%"
								xsl:use-attribute-sets="" >
								<fo:table-column column-width="52%"/>
								<fo:table-column column-width="1%"/>
								<fo:table-column column-width="1%"/>
								<fo:table-column column-width="46%"/>
									<fo:table-body>
										<fo:table-row>
											<fo:table-cell number-rows-spanned="" display-align="before" xsl:use-attribute-sets=""> <!-- PRIMERA COLUMNA-->
												<fo:block>
													<fo:table table-layout="fixed"
														width="100%"
														xsl:use-attribute-sets="" >
														<fo:table-column column-width="100%"/>
														<fo:table-body>
                                                            <fo:table-row>
                                                                <fo:table-cell>
                                                                    <fo:block>
                                                                        <xsl:if test="//Anulacion !=''">
                                                                            <fo:table table-layout="fixed"
                                                                                        width="100%"
                                                                                        xsl:use-attribute-sets="" >
                                                                                <fo:table-column column-width="93%"/>
                                                                                <fo:table-body>
                                                                                    <fo:table-row>
                                                                                        <fo:table-cell padding-left="0mm" padding-bottom="0.5mm" xsl:use-attribute-sets="TextoN01" background-color="" padding-top="0mm" margin-left="0cm">
                                                                                            <fo:block text-align="center">Anulación</fo:block>
                                                                                        </fo:table-cell>
                                                                                    </fo:table-row>
                                                                                    <fo:table-row>
                                                                                        <fo:table-cell height="0.5mm" padding-left="0mm" padding-bottom="0mm" xsl:use-attribute-sets="" background-color="#d3392d" padding-top="0mm">
                                                                                            <fo:block text-align="center"></fo:block>
                                                                                        </fo:table-cell>
                                                                                    </fo:table-row>
                                                                                    <fo:table-row>
                                                                                        <fo:table-cell padding-bottom="0.5mm" xsl:use-attribute-sets="  TextoN02" padding-left="0mm" padding-top="0.5mm" margin-left="0cm">
                                                                                            <fo:block text-align="left">Fecha: <fo:inline xsl:use-attribute-sets=" Texto01" color="black"><xsl:value-of select="//Anulacion/FechaAnulacion"/></fo:inline></fo:block>
                                                                                        </fo:table-cell>
                                                                                    </fo:table-row>
                                                                                    <fo:table-row>
                                                                                        <fo:table-cell padding-bottom="0.5mm" xsl:use-attribute-sets=" TextoN02" padding-left="0mm" margin-left="0cm">
                                                                                            <fo:block text-align="left">Motivo: <fo:inline xsl:use-attribute-sets="Texto01" color="black"><xsl:value-of select="//Anulacion/MotivoAnulacion"/></fo:inline></fo:block>
                                                                                        </fo:table-cell>
                                                                                    </fo:table-row>
                                                                                    <fo:table-row>
                                                                                        <fo:table-cell height="0.5mm" padding-left="0mm" padding-bottom="0mm" xsl:use-attribute-sets="TextoN02" background-color="#d3392d" padding-top="0mm">
                                                                                            <fo:block text-align="center"></fo:block>
                                                                                        </fo:table-cell>
                                                                                    </fo:table-row>
                                                                                    <fo:table-row>
                                                                                        <fo:table-cell height="3mm" padding-left="0mm" padding-bottom="0mm" xsl:use-attribute-sets="TextoN02" background-color="" padding-top="0mm">
                                                                                            <fo:block text-align="center"></fo:block>
                                                                                        </fo:table-cell>
                                                                                    </fo:table-row>
                                                                                </fo:table-body>
                                                                            </fo:table>
                                                                        </xsl:if>
                                                                    </fo:block>
                                                                </fo:table-cell>
                                                            </fo:table-row>
															<fo:table-row>
																<fo:table-cell xsl:use-attribute-sets="" display-align="" padding-top="" padding-left="0mm" margin-right="0mm">
																	<fo:block text-align="left">
																		<xsl:choose>
																			<xsl:when test="$TipoDocumento = '02' or $TipoDocumento = '03'">
																				<fo:table table-layout="fixed" width="100%">
                                                                                    <fo:table-column column-width="40%"/>
																					<fo:table-body>
																						<fo:table-row>
																							<fo:table-cell xsl:use-attribute-sets="TextoN02" padding-left="1mm" padding-top="1mm" padding-bottom="1mm" background-color="#6CB4D4" display-align="center">
																								<fo:block text-align="left" color="#FFFFFF">
																									APLICA A FACTURA
																								</fo:block>
																							</fo:table-cell>
																						</fo:table-row>
                                                                                        <fo:table-row>
																							<fo:table-cell xsl:use-attribute-sets="TextoN075" padding-left="0mm" padding-top="1.5mm" padding-bottom="0mm">
																								<fo:block text-align="left" color="">
																									Número:&#160;<fo:inline xsl:use-attribute-sets="TextoN075" color=""><xsl:value-of select="format-number(//IdentificacionDocumento/NumeroFacturaAfectada,'00000000')"/></fo:inline>	
																								</fo:block>
																							</fo:table-cell>
																						</fo:table-row>
                                                                                        <fo:table-row>
																							<fo:table-cell xsl:use-attribute-sets="TextoN075" padding-left="0mm" padding-top="0.5mm" padding-bottom="0mm">
																								<fo:block text-align="left" color="">
																									Fecha:&#160;<fo:inline xsl:use-attribute-sets="Texto075"><xsl:value-of select="translate(//IdentificacionDocumento/FechaFacturaAfectada,'/','-')"/></fo:inline>
																								</fo:block>
																							</fo:table-cell>
																						</fo:table-row>
																						<fo:table-row>
																							<fo:table-cell xsl:use-attribute-sets="TextoN075" padding-left="0mm" padding-top="0.5mm" padding-bottom="0mm">
																								<fo:block text-align="left" color="">
																									Monto Bs.:&#160;<fo:inline xsl:use-attribute-sets="Texto075">
																									<xsl:call-template name="IsZero">
																										<xsl:with-param name="valor"
																														select="//IdentificacionDocumento/MontoFacturaAfectada"/>
																										<xsl:with-param name="decimales"
																														select="2"/>
																									</xsl:call-template>
																									</fo:inline>
																								</fo:block>
																							</fo:table-cell>
																						</fo:table-row>
																						<fo:table-row>
																							<fo:table-cell height="" xsl:use-attribute-sets="TextoN075 " padding-left="0mm" padding-top="0.5mm" padding-bottom="0.75mm" display-align="before" padding-right="">
																								<fo:block text-align="left" color="" >
																									Comentario:&#160;<fo:inline xsl:use-attribute-sets="Texto075"><xsl:value-of select="//IdentificacionDocumento/ComentarioFacturaAfectada"/></fo:inline>
																								</fo:block>
																							</fo:table-cell>
																						</fo:table-row>
																					</fo:table-body>
																				</fo:table>
																			</xsl:when>
                                                                            <xsl:when test="$TipoDocumento = '01'">
                        
                                                                            </xsl:when>
                                                                            <xsl:when test="$TipoDocumento = '04'">
                                                                                <fo:table table-layout="fixed" width="100%">
                                                                                    <fo:table-column column-width="100%"/>
                                                                                    <fo:table-body>
                                                                                        <fo:table-row>
                                                                                            <fo:table-cell>
                                                                                                <fo:block>
                                                                                                    <fo:table table-layout="fixed" width="100%">
                                                                                                        <fo:table-column column-width="20%"/>
                                                                                                        <fo:table-column column-width="80%"/>
                                                                                                        <fo:table-body>
                                                                                                            <fo:table-row>
                                                                                                                <fo:table-cell height="" xsl:use-attribute-sets="TextoN075 " padding-left="0mm" padding-top="0.5mm" padding-bottom="0.75mm" display-align="before" padding-right="0cm">
                                                                                                                    <fo:block text-align="left" color="" >
                                                                                                                        Motivo Traslado:
                                                                                                                    </fo:block>
                                                                                                                </fo:table-cell>
                                                                                                                <fo:table-cell height="" xsl:use-attribute-sets="TextoN075 " padding-left="0mm" padding-top="0.5mm" padding-bottom="0.75mm" display-align="before" padding-right="0.5cm">
                                                                                                                    <fo:block text-align="left" color="" >
                                                                                                                      <fo:inline xsl:use-attribute-sets="Texto075"><xsl:value-of select="//GuiaDespacho/MotivoTraslado"/></fo:inline>
                                                                                                                    </fo:block>
                                                                                                                </fo:table-cell>
                                                                                                            </fo:table-row>
                                                                                                            <fo:table-row>
                                                                                                                <fo:table-cell height="0.5cm" xsl:use-attribute-sets="TextoN075 " padding-left="0mm" padding-top="0.5mm" padding-bottom="0.75mm" display-align="before" padding-right="0cm">
                                                                                                                    <fo:block text-align="left" color="" >
                                                                                                                        Origen Traslado:
                                                                                                                    </fo:block>
                                                                                                                </fo:table-cell>
                                                                                                                <fo:table-cell height="0.5cm" xsl:use-attribute-sets="TextoN075 " padding-left="0mm" padding-top="0.5mm" padding-bottom="0.75mm" display-align="before" padding-right="0.5cm">
                                                                                                                    <fo:block text-align="left" color="" >
                                                                                                                        <fo:inline xsl:use-attribute-sets="Texto075"><xsl:value-of select="//GuiaDespacho/OrigenProducto"/></fo:inline>
                                                                                                                    </fo:block>
                                                                                                                </fo:table-cell>
                                                                                                            </fo:table-row>
                                                                                                        </fo:table-body>
                                                                                                    </fo:table>
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row>
                                                                                            <fo:table-cell>
                                                                                                <fo:block>
                                                                                                    <fo:table table-layout="fixed" width="100%">
                                                                                                        <fo:table-column column-width="25%"/>
                                                                                                        <fo:table-column column-width="75%"/>
                                                                                                        <fo:table-body>
                                                                                                            <fo:table-row>
                                                                                                                <fo:table-cell height="" xsl:use-attribute-sets="TextoN075 " padding-left="0mm" padding-top="0.5mm" padding-bottom="0mm" display-align="before" padding-right="0cm">
                                                                                                                    <fo:block text-align="left" color="" >
                                                                                                                        Peso Total:
                                                                                                                    </fo:block>
                                                                                                                </fo:table-cell>
                                                                                                                <fo:table-cell height="" xsl:use-attribute-sets="TextoN075 " padding-left="0mm" padding-top="0.5mm" padding-bottom="0mm" display-align="before" padding-right="0.5cm">
                                                                                                                    <fo:block text-align="left" color="" >
                                                                                                                        <fo:inline xsl:use-attribute-sets="Texto075"><xsl:value-of select="//GuiaDespacho/MotivoTraslado"/></fo:inline>
                                                                                                                    </fo:block>
                                                                                                                </fo:table-cell>
                                                                                                            </fo:table-row>
                                                                                                            <fo:table-row>
                                                                                                                <fo:table-cell height="" xsl:use-attribute-sets="TextoN075 " padding-left="0mm" padding-top="0.5mm" padding-bottom="0mm" display-align="before" padding-right="0cm">
                                                                                                                    <fo:block text-align="left" color="" >
                                                                                                                        Tipo de Producto:
                                                                                                                    </fo:block>
                                                                                                                </fo:table-cell>
                                                                                                                <fo:table-cell height="" xsl:use-attribute-sets="TextoN075 " padding-left="0mm" padding-top="0.5mm" padding-bottom="0mm" display-align="before" padding-right="0.5cm">
                                                                                                                    <fo:block text-align="left" color="" >
                                                                                                                        <fo:inline xsl:use-attribute-sets="Texto075"><xsl:value-of select="//GuiaDespacho/TipoProducto"/></fo:inline>
                                                                                                                    </fo:block>
                                                                                                                </fo:table-cell>
                                                                                                            </fo:table-row>
                                                                                                            <fo:table-row>
                                                                                                                <fo:table-cell height="" xsl:use-attribute-sets="TextoN075 " padding-left="0mm" padding-top="0.5mm" padding-bottom="0mm" display-align="before" padding-right="0cm">
                                                                                                                    <fo:block text-align="left" color="" >
                                                                                                                        Descripción del Servicio:
                                                                                                                    </fo:block>
                                                                                                                </fo:table-cell>
                                                                                                                <fo:table-cell height="" xsl:use-attribute-sets="TextoN075 " padding-left="0mm" padding-top="0.5mm" padding-bottom="0mm" display-align="center" padding-right="0.5cm">
                                                                                                                    <fo:block text-align="left" color="" >
                                                                                                                        <fo:inline xsl:use-attribute-sets="Texto075"><xsl:value-of select="//GuiaDespacho/DescripcionServicio"/></fo:inline>
                                                                                                                    </fo:block>
                                                                                                                </fo:table-cell>
                                                                                                            </fo:table-row>
                                                                                                        </fo:table-body>
                                                                                                    </fo:table>
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>     
                                                                                    </fo:table-body>
                                                                                </fo:table>
                                                                            </xsl:when>
																		</xsl:choose>
																	</fo:block>
																</fo:table-cell>
															</fo:table-row>
														</fo:table-body>
													</fo:table>
												</fo:block>
											</fo:table-cell>
											<fo:table-cell xsl:use-attribute-sets="" display-align="after"> <!-- SEGUNDA COLUMNA-->
												<fo:block>
													<!-- <fo:table table-layout="fixed"
														width="100%"
														xsl:use-attribute-sets="" >
														<fo:table-column column-width="100%"/>
														<fo:table-body>
															<fo:table-row>
																<fo:table-cell xsl:use-attribute-sets="" margin-left="0mm" margin-right="0mm">
																	<fo:block>
                                                                        <xsl:choose>
                                                                            <xsl:when test="$MonedaBase !='USD'">
                                                                                <fo:table table-layout="fixed"
                                                                                    width="100%"
                                                                                    xsl:use-attribute-sets="" >
                                                                                    <fo:table-column column-width="54%"/>
                                                                                    <fo:table-column column-width="10%"/>
                                                                                    <fo:table-column column-width="36%"/>
                                                                                    <fo:table-body>
                                                                                        <fo:table-row>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Subtotal
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-left="0mm" padding-bottom="0.5mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="center" color="black">
                                                                                                    USD
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-right="0.5mm" padding-bottom="0.5mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    <xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/Subtotal != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/Subtotal"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Descuento
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-left="0mm" padding-bottom="0.5mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="center" color="black">
                                                                                                    USD
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-right="0.5mm" padding-bottom="0.5mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    <xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/TotalDescuento != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/TotalDescuento"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Base Imponible (G)
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="center" color="black">
                                                                                                    USD
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-right="0.5mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    <xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G'] != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G']/BaseImponibleImp"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>		
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Exento
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="center" color="black">
                                                                                                    USD
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-right="0.5mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    <xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/MontoExentoTotal != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/MontoExentoTotal"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>		
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Alícuota I.V.A. (16.00%)
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="center" color="black">
                                                                                                    USD
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-right="0.5mm" padding-top="0mm" padding-bottom="0.5mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    <xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G'] != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G']/ValorTotalImp"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>		
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row> 
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0.35mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Base Imponible (IGTF)
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="center" color="black">
                                                                                                    USD
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-right="0.35mm" padding-top="0mm" padding-bottom="0.5mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    <xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='IGTF'] != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='IGTF']/BaseImponibleImp"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>		
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0.35mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Alícuota IGTF (3.00%)
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="center" color="black">
                                                                                                    USD
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-right="0.35mm" padding-top="0mm" padding-bottom="0.5mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    <xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='IGTF'] != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='IGTF']/ValorTotalImp"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>		
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row>
                                                                                            <fo:table-cell number-columns-spanned="3" display-align="center">
                                                                                                <fo:block border-style="solid"
                                                                                                            border-width="0.6"
                                                                                                            fox:border-radius="" 
                                                                                                            text-align="center"
                                                                                                            background-color="#19452C"
                                                                                                            border-top-color="#19452C"
                                                                                                            border-bottom-color="#19452C"
                                                                                                            border-left-color="#19452C"
                                                                                                            border-right-color="#19452C">
                                                                                                    <fo:table table-layout="fixed"
                                                                                                        width="100%"
                                                                                                        xsl:use-attribute-sets="" >
                                                                                                        <fo:table-column column-width="100%"/>
                                                                                                        <fo:table-body>
                                                                                                            <fo:table-row>
                                                                                                                <fo:table-cell display-align="center">
                                                                                                                    <fo:block>
                                                                                                                        <fo:table table-layout="fixed"
                                                                                                                            width="100%"
                                                                                                                            xsl:use-attribute-sets="" >
                                                                                                                            <fo:table-column column-width="54%"/>
                                                                                                                            <fo:table-column column-width="10%"/>
                                                                                                                            <fo:table-column column-width="36%"/>
                                                                                                                            <fo:table-body>
                                                                                                                                <fo:table-row>
                                                                                                                                    <fo:table-cell xsl:use-attribute-sets="TextoN02" display-align="center" padding-top="1.5mm" padding-bottom="1.25mm" padding-left="0.5mm">
                                                                                                                                        <fo:block text-align="left" color="white">
                                                                                                                                            Total A Pagar
                                                                                                                                        </fo:block>
                                                                                                                                    </fo:table-cell>
                                                                                                                                    <fo:table-cell xsl:use-attribute-sets="TextoN02" display-align="center" padding-top="1.5mm" padding-bottom="1.25mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                                                        <fo:block text-align="center" color="white">
                                                                                                                                            USD
                                                                                                                                        </fo:block>
                                                                                                                                    </fo:table-cell>
                                                                                                                                    <fo:table-cell xsl:use-attribute-sets="TextoN02" display-align="center" padding-top="1.5mm" padding-bottom="1.25mm" padding-right="0.5mm">
                                                                                                                                        <fo:block text-align="right" color="white">
                                                                                                                                            <xsl:choose>
                                                                                                                                                <xsl:when test="//TotalesOtraMoneda/TotalAPagar != ''">
                                                                                                                                                    <xsl:call-template name="IsZero">
                                                                                                                                                        <xsl:with-param name="valor"
                                                                                                                                                                        select="//TotalesOtraMoneda/TotalAPagar"/>
                                                                                                                                                        <xsl:with-param name="decimales"
                                                                                                                                                                        select="2"/>
                                                                                                                                                    </xsl:call-template>
                                                                                                                                                </xsl:when>
                                                                                                                                                <xsl:otherwise>
                                                                                                                                                    0.00
                                                                                                                                                </xsl:otherwise>
                                                                                                                                            </xsl:choose>				
                                                                                                                                        </fo:block>
                                                                                                                                    </fo:table-cell>
                                                                                                                                </fo:table-row>
                                                                                                                            </fo:table-body>
                                                                                                                        </fo:table>
                                                                                                                    </fo:block>
                                                                                                                </fo:table-cell>
                                                                                                            </fo:table-row>
                                                                                                        </fo:table-body>
                                                                                                    </fo:table>
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                    </fo:table-body>
                                                                                </fo:table>
                                                                            </xsl:when>
                                                                            <xsl:otherwise>
                                                                                <fo:table table-layout="fixed"
                                                                                    width="100%"
                                                                                    xsl:use-attribute-sets="" >
                                                                                    <fo:table-column column-width="54%"/>
                                                                                    <fo:table-column column-width="10%"/>
                                                                                    <fo:table-column column-width="36%"/>
                                                                                    <fo:table-body>
                                                                                        <fo:table-row>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Subtotal
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-left="0mm" padding-bottom="0.5mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="center" color="black">
                                                                                                    Bs.
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-right="0.5mm" padding-bottom="0.5mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    <xsl:choose>
                                                                                                        <xsl:when test="//Totales/Subtotal != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/Subtotal"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Descuento
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-left="0mm" padding-bottom="0.5mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="center" color="black">
                                                                                                    Bs.
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-right="0.5mm" padding-bottom="0.5mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    <xsl:choose>
                                                                                                        <xsl:when test="//Totales/TotalDescuento != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/TotalDescuento"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Base Imponible (G)
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="center" color="black">
                                                                                                    Bs.
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-right="0.5mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    <xsl:choose>
                                                                                                        <xsl:when test="//Totales/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G'] != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G']/BaseImponibleImp"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>		
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Exento
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="center" color="black">
                                                                                                    Bs.
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-right="0.5mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    <xsl:choose>
                                                                                                        <xsl:when test="//Totales/MontoExentoTotal != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/MontoExentoTotal"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>		
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Alícuota I.V.A. (16.00%)
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="center" color="black">
                                                                                                    Bs.
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-right="0.5mm" padding-top="0mm" padding-bottom="0.5mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    <xsl:choose>
                                                                                                        <xsl:when test="//Totales/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G'] != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G']/ValorTotalImp"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>		
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row> 
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0.35mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Base Imponible (IGTF)
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="center" color="black">
                                                                                                    Bs.
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-right="0.35mm" padding-top="0mm" padding-bottom="0.5mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    <xsl:choose>
                                                                                                        <xsl:when test="//Totales/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='IGTF'] != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='IGTF']/BaseImponibleImp"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>		
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0.35mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Alícuota IGTF (3.00%)
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0mm" padding-bottom="0.5mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="center" color="black">
                                                                                                    Bs.
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-right="0.35mm" padding-top="0mm" padding-bottom="0.5mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    <xsl:choose>
                                                                                                        <xsl:when test="//Totales/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='IGTF'] != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='IGTF']/ValorTotalImp"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>		
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row>
                                                                                            <fo:table-cell number-columns-spanned="3" display-align="center">
                                                                                                <fo:block border-style="solid"
                                                                                                            border-width="0.6"
                                                                                                            fox:border-radius="" 
                                                                                                            text-align="center"
                                                                                                            background-color="#19452C"
                                                                                                            border-top-color="#19452C"
                                                                                                            border-bottom-color="#19452C"
                                                                                                            border-left-color="#19452C"
                                                                                                            border-right-color="#19452C">
                                                                                                    <fo:table table-layout="fixed"
                                                                                                        width="100%"
                                                                                                        xsl:use-attribute-sets="" >
                                                                                                        <fo:table-column column-width="100%"/>
                                                                                                        <fo:table-body>
                                                                                                            <fo:table-row>
                                                                                                                <fo:table-cell display-align="center">
                                                                                                                    <fo:block>
                                                                                                                        <fo:table table-layout="fixed"
                                                                                                                            width="100%"
                                                                                                                            xsl:use-attribute-sets="" >
                                                                                                                            <fo:table-column column-width="54%"/>
                                                                                                                            <fo:table-column column-width="10%"/>
                                                                                                                            <fo:table-column column-width="36%"/>
                                                                                                                            <fo:table-body>
                                                                                                                                <fo:table-row>
                                                                                                                                    <fo:table-cell xsl:use-attribute-sets="TextoN02" display-align="center" padding-top="1.5mm" padding-bottom="1.25mm" padding-left="0.5mm">
                                                                                                                                        <fo:block text-align="left" color="white">
                                                                                                                                            Total A Pagar
                                                                                                                                        </fo:block>
                                                                                                                                    </fo:table-cell>
                                                                                                                                    <fo:table-cell xsl:use-attribute-sets="TextoN02" display-align="center" padding-top="1.5mm" padding-bottom="1.25mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                                                        <fo:block text-align="center" color="white">
                                                                                                                                            Bs.
                                                                                                                                        </fo:block>
                                                                                                                                    </fo:table-cell>
                                                                                                                                    <fo:table-cell xsl:use-attribute-sets="TextoN02" display-align="center" padding-top="1.5mm" padding-bottom="1.25mm" padding-right="0.5mm">
                                                                                                                                        <fo:block text-align="right" color="white">
                                                                                                                                            <xsl:choose>
                                                                                                                                                <xsl:when test="//Totales/TotalAPagar != ''">
                                                                                                                                                    <xsl:call-template name="IsZero">
                                                                                                                                                        <xsl:with-param name="valor"
                                                                                                                                                                        select="//Totales/TotalAPagar"/>
                                                                                                                                                        <xsl:with-param name="decimales"
                                                                                                                                                                        select="2"/>
                                                                                                                                                    </xsl:call-template>
                                                                                                                                                </xsl:when>
                                                                                                                                                <xsl:otherwise>
                                                                                                                                                    0.00
                                                                                                                                                </xsl:otherwise>
                                                                                                                                            </xsl:choose>				
                                                                                                                                        </fo:block>
                                                                                                                                    </fo:table-cell>
                                                                                                                                </fo:table-row>
                                                                                                                            </fo:table-body>
                                                                                                                        </fo:table>
                                                                                                                    </fo:block>
                                                                                                                </fo:table-cell>
                                                                                                            </fo:table-row>
                                                                                                        </fo:table-body>
                                                                                                    </fo:table>
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                    </fo:table-body>
                                                                                </fo:table>
                                                                            </xsl:otherwise>
                                                                        </xsl:choose>
																	</fo:block>
																</fo:table-cell>
															</fo:table-row>
														</fo:table-body>
													</fo:table> -->
												</fo:block>
											</fo:table-cell>	
											<fo:table-cell xsl:use-attribute-sets="" display-align="after"> <!-- TERCERA COLUMNA-->
												<fo:block>
													
												</fo:block>
											</fo:table-cell>	
											<fo:table-cell xsl:use-attribute-sets="" display-align="after"> <!-- CUARTA COLUMNA-->
												<fo:block>
													<fo:table table-layout="fixed"
														width="100%"
														xsl:use-attribute-sets="" >
														<fo:table-column column-width="100%"/>
														<fo:table-body>
															<fo:table-row>
																<fo:table-cell xsl:use-attribute-sets="" margin-left="0mm" margin-right="0mm">
																	<fo:block>
                                                                        <xsl:choose>
                                                                            <xsl:when test="$MonedaBase !='USD'">
                                                                                <fo:table table-layout="fixed"
                                                                                    width="100%"
                                                                                    xsl:use-attribute-sets="" >
                                                                                    <fo:table-column column-width="50%"/>
                                                                                    <fo:table-column column-width="24%"/>
                                                                                    <fo:table-column column-width="26%"/>
                                                                                    <fo:table-body>
                                                                                        <fo:table-row>
                                                                                            <fo:table-cell number-columns-spanned="3" xsl:use-attribute-sets="BordeTR">
                                                                                                <fo:block>
                                                                                                    <fo:table table-layout="fixed"
                                                                                                        width="100%"
                                                                                                        xsl:use-attribute-sets="" >
                                                                                                        <fo:table-column column-width="40%"/>
                                                                                                        <fo:table-column column-width="34%"/>
                                                                                                        <fo:table-body>
                                                                                                            <fo:table-row xsl:use-attribute-sets="">
                                                                                                                <fo:table-cell display-align="center" xsl:use-attribute-sets="Texto02" padding-top="1mm" padding-bottom="2mm" margin-right="0mm" margin-left="0mm">
                                                                                                                    <fo:block text-align="left">
                                                                                                                        Tasa de Cambio (<xsl:value-of select="translate(//Encabezado/IdentificacionDocumento/FechaEmision, '/','-')"/>)
                                                                                                                    </fo:block>
                                                                                                                </fo:table-cell>
                                                                                                                <fo:table-cell display-align="center" xsl:use-attribute-sets="Texto02" padding-top="1mm" padding-bottom="2mm" margin-right="0mm" margin-left="0mm">
                                                                                                                    <fo:block text-align="right">
                                                                                                                        Bs.&#160;<xsl:call-template name="IsZero4Decimales">
                                                                                                                            <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/TipoCambio"/>
                                                                                                                            <xsl:with-param name="decimales"
                                                                                                                                            select="4"/>
                                                                                                                        </xsl:call-template> * 1 USD
                                                                                                                    </fo:block>
                                                                                                                </fo:table-cell>
                                                                                                            </fo:table-row>
                                                                                                        </fo:table-body>
                                                                                                    </fo:table>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row xsl:use-attribute-sets="BordeTR">
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Sub total
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-left="0mm" padding-bottom="0.75mm" margin-left="0mm" margin-right="0mm">
                                                                                               <fo:block text-align="right" color="black">
                                                                                                    $&#160;<xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/Subtotal != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/Subtotal"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-right="0.5mm" padding-bottom="0.75mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    Bs.&#160;<xsl:choose>
                                                                                                        <xsl:when test="//Totales/Subtotal != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/Subtotal"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row xsl:use-attribute-sets="BordeTR">
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Descuento
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-left="0mm" padding-bottom="0.75mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    <fo:block text-align="right" color="black">
                                                                                                    $&#160;<xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/TotalDescuento != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/TotalDescuento"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-right="0.5mm" padding-bottom="0.75mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    Bs.&#160;<xsl:choose>
                                                                                                        <xsl:when test="//Totales/TotalDescuento != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/TotalDescuento"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row xsl:use-attribute-sets="BordeTR">
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Base Imponible (G)
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    $&#160;<xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G'] != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G']/BaseImponibleImp"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-right="0.5mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    Bs.&#160;<xsl:choose>
                                                                                                        <xsl:when test="//Totales/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G'] != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G']/BaseImponibleImp"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>		
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row xsl:use-attribute-sets="BordeTR">
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Exento
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    $&#160;<xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/MontoExentoTotal != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/MontoExentoTotal"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-right="0.5mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    Bs.&#160;<xsl:choose>
                                                                                                        <xsl:when test="//Totales/MontoExentoTotal != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/MontoExentoTotal"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>		
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row xsl:use-attribute-sets="BordeTR">
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Alícuota I.V.A. (16.00%)
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    $&#160;<xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G'] != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G']/ValorTotalImp"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-right="0.5mm" padding-top="0.75mm" padding-bottom="0.75mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    Bs.&#160;<xsl:choose>
                                                                                                        <xsl:when test="//Totales/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G'] != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G']/ValorTotalImp"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>		
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row xsl:use-attribute-sets="BordeTR">
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Total Operación
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    $&#160;<xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/MontoTotalConIVA != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/MontoTotalConIVA"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-right="0.5mm" padding-top="0.75mm" padding-bottom="0.75mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    Bs.&#160;<xsl:choose>
                                                                                                        <xsl:when test="//Totales/MontoTotalConIVA != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/MontoTotalConIVA"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>		
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row xsl:use-attribute-sets="BordeTR">
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    IGTF Percibido 3.00% de <xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='IGTF'] != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='IGTF']/BaseImponibleImp"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    $&#160;<xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='IGTF'] != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='IGTF']/ValorTotalImp"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-right="0.35mm" padding-top="0.75mm" padding-bottom="0.75mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    Bs.&#160;<xsl:choose>
                                                                                                        <xsl:when test="//Totales/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='IGTF'] != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='IGTF']/ValorTotalImp"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>		
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row xsl:use-attribute-sets="BordeTR">
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Total A Pagar
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    $&#160;<xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/TotalAPagar != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/TotalAPagar"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-right="0.5mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    Bs.&#160;<xsl:choose>
                                                                                                        <xsl:when test="//Totales/TotalAPagar != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/TotalAPagar"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>				
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <!-- <fo:table-row xsl:use-attribute-sets="BordeTR">
                                                                                            <fo:table-cell number-columns-spanned="3" display-align="center">
                                                                                                <fo:block border-style=""
                                                                                                            border-width=""
                                                                                                            fox:border-radius="" 
                                                                                                            text-align="center"
                                                                                                            background-color=""
                                                                                                            border-top-color=""
                                                                                                            border-bottom-color=""
                                                                                                            border-left-color=""
                                                                                                            border-right-color="">
                                                                                                    <fo:table table-layout="fixed"
                                                                                                        width="100%"
                                                                                                        xsl:use-attribute-sets="" >
                                                                                                        <fo:table-column column-width="100%"/>
                                                                                                        <fo:table-body>
                                                                                                            <fo:table-row>
                                                                                                                <fo:table-cell display-align="center">
                                                                                                                    <fo:block>
                                                                                                                        <fo:table table-layout="fixed"
                                                                                                                            width="100%"
                                                                                                                            xsl:use-attribute-sets="" >
                                                                                                                            <fo:table-column column-width="48%"/>
                                                                                                                            <fo:table-column column-width="16%"/>
                                                                                                                            <fo:table-column column-width="36%"/>
                                                                                                                            <fo:table-body>
                                                                                                                                
                                                                                                                            </fo:table-body>
                                                                                                                        </fo:table>
                                                                                                                    </fo:block>
                                                                                                                </fo:table-cell>
                                                                                                            </fo:table-row>
                                                                                                        </fo:table-body>
                                                                                                    </fo:table>
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row> -->
                                                                                    </fo:table-body>
                                                                                </fo:table>
                                                                            </xsl:when>
                                                                            <xsl:otherwise>
                                                                                <fo:table table-layout="fixed"
                                                                                    width="100%"
                                                                                    xsl:use-attribute-sets="" >
                                                                                    <fo:table-column column-width="50%"/>
                                                                                    <fo:table-column column-width="24%"/>
                                                                                    <fo:table-column column-width="26%"/>
                                                                                    <fo:table-body>
                                                                                        <fo:table-row>
                                                                                            <fo:table-cell number-columns-spanned="3">
                                                                                                <fo:block>
                                                                                                    <fo:table table-layout="fixed"
                                                                                                        width="100%"
                                                                                                        xsl:use-attribute-sets="" >
                                                                                                        <fo:table-column column-width="40%"/>
                                                                                                        <fo:table-column column-width="34%"/>
                                                                                                        <fo:table-body>
                                                                                                            <fo:table-row>
                                                                                                                <fo:table-cell display-align="center" xsl:use-attribute-sets="Texto02" padding-top="1mm" padding-bottom="2mm" margin-right="0mm" margin-left="0mm">
                                                                                                                    <fo:block text-align="left">
                                                                                                                        Tasa de Cambio (<xsl:value-of select="translate(//Encabezado/IdentificacionDocumento/FechaEmision, '/','-')"/>)
                                                                                                                    </fo:block>
                                                                                                                </fo:table-cell>
                                                                                                                <fo:table-cell display-align="center" xsl:use-attribute-sets="Texto02" padding-top="1mm" padding-bottom="2mm" margin-right="0mm" margin-left="0mm">
                                                                                                                    <fo:block text-align="right">
                                                                                                                        Bs.&#160;<xsl:call-template name="IsZero4Decimales">
                                                                                                                            <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/TipoCambio"/>
                                                                                                                            <xsl:with-param name="decimales"
                                                                                                                                            select="4"/>
                                                                                                                        </xsl:call-template> * 1 USD
                                                                                                                    </fo:block>
                                                                                                                </fo:table-cell>
                                                                                                            </fo:table-row>
                                                                                                        </fo:table-body>
                                                                                                    </fo:table>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row xsl:use-attribute-sets="BordeTR">
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Sub total
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-left="0mm" padding-bottom="0.75mm" margin-left="0mm" margin-right="0mm">
                                                                                               <fo:block text-align="right" color="black">
                                                                                                    Bs.&#160;<xsl:choose>
                                                                                                        <xsl:when test="//Totales/Subtotal != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/Subtotal"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-right="0.5mm" padding-bottom="0.75mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    $&#160;<xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/Subtotal != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/Subtotal"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row xsl:use-attribute-sets="BordeTR">
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Descuento
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-left="0mm" padding-bottom="0.75mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    Bs.&#160;<xsl:choose>
                                                                                                        <xsl:when test="//Totales/TotalDescuento != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/TotalDescuento"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-right="0.5mm" padding-bottom="0.75mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    $&#160;<xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/TotalDescuento != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/TotalDescuento"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row xsl:use-attribute-sets="BordeTR">
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Base Imponible (G)
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    Bs.&#160;<xsl:choose>
                                                                                                        <xsl:when test="//Totales/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G'] != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G']/BaseImponibleImp"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-right="0.5mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    $&#160;<xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G'] != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G']/BaseImponibleImp"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row xsl:use-attribute-sets="BordeTR">
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Exento
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    Bs.&#160;<xsl:choose>
                                                                                                        <xsl:when test="//Totales/MontoExentoTotal != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/MontoExentoTotal"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>		
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" background-color="" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-right="0.5mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    $&#160;<xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/MontoExentoTotal != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/MontoExentoTotal"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row xsl:use-attribute-sets="BordeTR">
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Alícuota I.V.A. (16.00%)
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    Bs.&#160;<xsl:choose>
                                                                                                        <xsl:when test="//Totales/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G'] != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G']/ValorTotalImp"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-right="0.5mm" padding-top="0.75mm" padding-bottom="0.75mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    $&#160;<xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G'] != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='G']/ValorTotalImp"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>			
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row xsl:use-attribute-sets="BordeTR">
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Total Operación
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    Bs.&#160;<xsl:choose>
                                                                                                        <xsl:when test="//Totales/MontoTotalConIVA != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/MontoTotalConIVA"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-right="0.5mm" padding-top="0.75mm" padding-bottom="0.75mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    $&#160;<xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/MontoTotalConIVA != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/MontoTotalConIVA"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>			
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row xsl:use-attribute-sets="BordeTR">
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    IGTF Percibido 3.00% de <xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='IGTF'] != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='IGTF']/BaseImponibleImp"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    Bs.&#160;<xsl:choose>
                                                                                                        <xsl:when test="//Totales/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='IGTF'] != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='IGTF']/ValorTotalImp"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>		
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-right="0.35mm" padding-top="0.75mm" padding-bottom="0.75mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    $&#160;<xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='IGTF'] != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/ImpuestosSubtotal/ImpuestoSubtotal[CodigoTotalImp='IGTF']/ValorTotalImp"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <fo:table-row xsl:use-attribute-sets="BordeTR">
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0.5mm">
                                                                                                <fo:block text-align="left" color="black">
                                                                                                    Total A Pagar
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-left="0mm" margin-left="0mm" margin-right="0mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    Bs.&#160;<xsl:choose>
                                                                                                        <xsl:when test="//Totales/TotalAPagar != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//Totales/TotalAPagar"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>	
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                            <fo:table-cell xsl:use-attribute-sets="Texto02" display-align="center" padding-top="0.75mm" padding-bottom="0.75mm" padding-right="0.5mm">
                                                                                                <fo:block text-align="right" color="black">
                                                                                                    $&#160;<xsl:choose>
                                                                                                        <xsl:when test="//TotalesOtraMoneda/TotalAPagar != ''">
                                                                                                            <xsl:call-template name="IsZero">
                                                                                                                <xsl:with-param name="valor"
                                                                                                                                select="//TotalesOtraMoneda/TotalAPagar"/>
                                                                                                                <xsl:with-param name="decimales"
                                                                                                                                select="2"/>
                                                                                                            </xsl:call-template>
                                                                                                        </xsl:when>
                                                                                                        <xsl:otherwise>
                                                                                                            0.00
                                                                                                        </xsl:otherwise>
                                                                                                    </xsl:choose>				
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row>
                                                                                        <!-- <fo:table-row xsl:use-attribute-sets="BordeTR">
                                                                                            <fo:table-cell number-columns-spanned="3" display-align="center">
                                                                                                <fo:block border-style=""
                                                                                                            border-width=""
                                                                                                            fox:border-radius="" 
                                                                                                            text-align="center"
                                                                                                            background-color=""
                                                                                                            border-top-color=""
                                                                                                            border-bottom-color=""
                                                                                                            border-left-color=""
                                                                                                            border-right-color="">
                                                                                                    <fo:table table-layout="fixed"
                                                                                                        width="100%"
                                                                                                        xsl:use-attribute-sets="" >
                                                                                                        <fo:table-column column-width="100%"/>
                                                                                                        <fo:table-body>
                                                                                                            <fo:table-row>
                                                                                                                <fo:table-cell display-align="center">
                                                                                                                    <fo:block>
                                                                                                                        <fo:table table-layout="fixed"
                                                                                                                            width="100%"
                                                                                                                            xsl:use-attribute-sets="" >
                                                                                                                            <fo:table-column column-width="48%"/>
                                                                                                                            <fo:table-column column-width="16%"/>
                                                                                                                            <fo:table-column column-width="36%"/>
                                                                                                                            <fo:table-body>
                                                                                                                                
                                                                                                                            </fo:table-body>
                                                                                                                        </fo:table>
                                                                                                                    </fo:block>
                                                                                                                </fo:table-cell>
                                                                                                            </fo:table-row>
                                                                                                        </fo:table-body>
                                                                                                    </fo:table>
                                                                                                </fo:block>
                                                                                            </fo:table-cell>
                                                                                        </fo:table-row> -->
                                                                                    </fo:table-body>
                                                                                </fo:table>
                                                                            </xsl:otherwise>
                                                                        </xsl:choose>
																	</fo:block>
																</fo:table-cell>
															</fo:table-row>
														</fo:table-body>
													</fo:table>
												</fo:block>
											</fo:table-cell>	
										</fo:table-row>
                                        <fo:table-row>
                                            <fo:table-cell xsl:use-attribute-sets="" number-columns-spanned="4">
                                                <fo:block>
                                                    <fo:table table-layout="fixed" width="100%">
                                                        <fo:table-column column-width="11%"/>
                                                        <fo:table-column column-width="37%"/>
                                                        <fo:table-column column-width="52%"/>
                                                        <fo:table-body>
                                                            <fo:table-row>
                                                                <fo:table-cell display-align="before" xsl:use-attribute-sets="" padding-top="0.5mm" padding-right="1mm">
                                                                    <fo:block >
                                                                        <fo:external-graphic content-width="scale-to-fit" 
                                                                            height="2cm" 
                                                                            width="2cm" 
                                                                            scaling="uniform" 
                                                                            src="url('data:image/png;base64,{$EncabezadoImagen}')" />
                                                                    </fo:block>
                                                                </fo:table-cell>
                                                                <fo:table-cell display-align="center" xsl:use-attribute-sets="Texto08" >
                                                                    <fo:block text-align="justify">
                                                                        ¡Descubra todo lo que Lebomar tiene para usted! Escanee el código
                                                                        QR para explorar nuestras redes sociales, conocer nuestros nuevos
                                                                        productos y manténgase al día con nuestras soluciones tecnológicas.
                                                                    </fo:block>
                                                                </fo:table-cell>
                                                                <fo:table-cell padding-left="" padding-top="">
                                                                    <fo:block text-align="right">
                                                                        <fo:external-graphic content-width="100%"
                                                                                            height="1.2cm" vertical-align="middle"
                                                                                            scaling="uniform"
                                                                                            src="url('data:image/png;base64,{$PiePagImagen}')" />
                                                                    </fo:block>
                                                                </fo:table-cell>
                                                            </fo:table-row>
                                                        </fo:table-body>
                                                    </fo:table>
                                                </fo:block>
                                            </fo:table-cell>
                                        </fo:table-row>
                                        <fo:table-row>
                                            <fo:table-cell number-columns-spanned="4" padding-top="1mm">
                                                <fo:block margin-left="">
                                                    <fo:table table-layout="fixed"
                                                        width="100%"
                                                        xsl:use-attribute-sets="" >
                                                        <fo:table-column column-width="100%"/>
                                                        <fo:table-body>
                                                            <fo:table-row>
                                                                <fo:table-cell display-align="before" padding-left="0mm" padding-top="3mm" padding-bottom="0.5mm" xsl:use-attribute-sets="Texto08">
                                                                    <fo:block text-align="justify" >
                                                                        Este pago estará sujeto al cobro adicional del 3,00% del Impuesto a las Grandes Transacciones Financieras (IGTF), de conformidad con la Providencia Administrativa SNAT/2022/000013 publicada en la G.O.N 42.339 del 17-03-2022, en caso de ser cancelado en divisas. No aplica en pago en Bs.
                                                                    </fo:block>
                                                                </fo:table-cell>
                                                            </fo:table-row>
                                                            <fo:table-row>
                                                                <fo:table-cell display-align="before" padding-left="0mm" padding-top="1.5mm" padding-bottom="1.5mm" xsl:use-attribute-sets="Texto08" margin-left="0cm">
                                                                    <fo:block text-align="justify" >
                                                                        Este documento se expresa en 
                                                                        <xsl:choose>
                                                                            <xsl:when test="$MonedaBase = 'USD'">
                                                                                Dólares Americanos
                                                                            </xsl:when>
                                                                            <xsl:otherwise>
                                                                                Bolívares
                                                                            </xsl:otherwise>
                                                                        </xsl:choose>
                                                                        con su equivalente en 
                                                                        <xsl:choose>
                                                                            <xsl:when test="$MonedaBase = 'USD'">
                                                                                Bolívares
                                                                            </xsl:when>
                                                                            <xsl:otherwise>
                                                                                Dólares Americanos
                                                                            </xsl:otherwise>
                                                                        </xsl:choose>
                                                                        al tipo de cambio corriente del mercado a la fecha de su emisión, según lo establecido en el articulo 13 numeral 14 de la Providencia Administrativa SNAT /20244/0071 (..) en concordancia con el artículo 128  de la Ley del Banco Central de Venezuela (BCV); artículo 25 de la Ley que establece el Impuesto al Valor Agregado (IVA) y 38 del Reglamento General de la Ley que establece el Impuesto al Valor Agregado (RLIVA).
                                                                    </fo:block>
                                                                </fo:table-cell>
                                                            </fo:table-row>
                                                        </fo:table-body>
                                                    </fo:table>  
                                                </fo:block>
                                            </fo:table-cell>
                                        </fo:table-row>
										
									</fo:table-body>
							</fo:table>			
						</fo:block>
					</fo:block>
				</fo:flow>
			</fo:page-sequence>
		</fo:root>
	</xsl:template>
</xsl:stylesheet>