Liquid es un motor de templates que fue creado con requerimientos bien específicos

* Tiene que tener un markup simple y resultados hermosos. No es divertido usar motores de template que no produzcan resultados lindos.
* Debe ser no-ejecutable y seguro. Los usuarios pueden editar templates Liquid. Pero no quieres ejecutar código en tu servidor que haya sido escrito por tus usuarios. 
* Debe ser stateless (No debe guardar estado). Los pasos de compilación y renderización deben quedar separados, para que el (costoso) parseo y la compilación se haga solo una vez. Luego, puedes renderizar HTML con solo pasar un hash con variables locales y objetos. 
* Debe ser posible darle estilo tanto a Emails como a HTML. 
 

h2. Cosas a leer, mirar, etc.

* [[ES-Liquid para Programadores]] 
* [[ES-Liquid para Disenadores]] 
* [[ES-Usando Liquid sin Rails]]

* "Liquid":http://railscasts.com/episodes/118-liquid (screencast en Inglés)

h2. Quién usa Liquid? 

* "Shopify":http://www.shopify.com
* "Mephisto":http://mephistoblog.com/
* "Chameleon":http://chameleon.wikidot.com/
* "Cashboard":http://www.getcashboard.com
* "Edicy":http://www.edicy.com
* "Workory":http://www.workory.com
* "Zendesk":http://www.zendesk.com
* "SandwichBoard":http://www.sandwichboard.com/
* "YikeSite (CMS)":http://www.yikesite.com/
* "Simplicant (Applicant Tracking System)":http://www.simplicant.com/
* "3scale (API Management System)":http://www.3scale.net/
* "Chaptercore":http://www.chaptercore.com
* "ScreenSteps Live":http://bluemangolearning.com/screenstepslive
* "PokerAffiliateSolutions":http://www.pokeraffiliatesolutions.com/
* "Assistly":http://www.assistly.com
* "Ronin":http://www.roninapp.com
* "CrowdVine":http://www.crowdvine.com
* "AboutOne":http://www.aboutone.com
* "RightScale":http://support.rightscale.com/15-References/Liquid_Markup_with_RightScale_Widgets
* "Menumill":http://www.menumill.com
* "留级生":http://baddogai.github.com
* "Moxie Software":http://www.moxiesoft.com/
* "Rusic":http://rusic.com/
* "Ombu Shop":http://ombushop.com/
* ...Add yours :)

h2. ¿Por qué debería usar Liquid? 

* Quieres permitir que tus usuarios editen la apariencia de tu aplicación, pero no quieres que ejecuten código inseguro en tu servidor.
* Quieres renderizar templates directamente de tu base de datos.
* Te gusta motores de templates con el estilo Smarty.
* Necesitas un motor de template que funcione tan bien con HTML como con Emails.
* No te gusta el lenguaje de markup de tu actual motor de templates.
