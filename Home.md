Liquid is a template engine which was crafted for very specific requirements

* It has to have simple markup and beautiful results. Template engines which
  don't produce good looking results are no fun to use.
* It needs to be non-evaling and secure. Liquid templates are made so that users
  can edit them. You don't want your server running code that your users
  wrote.
* It has to be stateless. The compile and render steps have to be separate, so
  that the expensive parsing and compiling can be done once;  later on, you can
  just render it by passing in a hash with local variables and objects.
* It needs to be able to style emails as well as HTML.

## Stuff to read, watch, etc.

* [Class reference](http://rubydoc.info/gems/liquid)
* [[Liquid for Programmers]]
* [[Liquid for Designers]]
* [Liquid screencast](http://railscasts.com/episodes/118-liquid)
* [[Ports of Liquid to other environments]]

## Who uses Liquid?

* [Shopify](http://www.shopify.com)
* [eLocal](http://www.elocal.com)
* [Mephisto](http://mephistoblog.com/)
* [Harmony](http://get.harmonyapp.com)
* [Chameleon](http://chameleon.wikidot.com/)
* [Cashboard](http://www.getcashboard.com)
* [Adobe Business Catalyst](http://businesscatalyst.com/)
* [Voog](http://www.voog.com)
* [Zendesk](http://www.zendesk.com)
* [YikeSite (CMS)](http://api.yikesite.com/)
* [Simplicant (Applicant Tracking System)](http://www.simplicant.com/)
* [3scale (API Management System)](http://www.3scale.net/)
* [Chaptercore](http://www.chaptercore.com)
* [ScreenSteps Live](http://bluemangolearning.com/screenstepslive)
* [PokerAffiliateSolutions](http://www.pokeraffiliatesolutions.com/)
* [Desk.com](http://www.desk.com)
* [Ronin](http://www.roninapp.com)
* [AboutOne](http://www.aboutone.com)
* [RightScale](http://support.rightscale.com/15-References/Liquid_Markup_with_RightScale_Widgets)
* [Menumill](http://www.menumill.com)
* [Moxie Software](http://www.moxiesoft.com/)
* [Rusic](http://rusic.com/)
* [Development Seed](http://developmentseed.org/blog/2011/09/09/jekyll-github-pages/)
* [peerTransfer](http://peertransfer.com)
* [NationBuilder](http://nationbuilder.com/)
* [Avenue](http://www.prontoavenue.biz)
* [Device Magic](http://www.devicemagic.com)
* [Spiceworks](http://www.spiceworks.com)
* [PufferPages (CMS)](https://github.com/puffer/puffer_pages/)
* [Displet](http://displet.com)
* [Paspartout](http://paspartout.com)
* [TrackGrid](http://www.trackgrid.com)
* [Jekyll](http://jekyllrb.com/)
* [Octopress](http://octopress.org/)
* [Vnda](http://www.vnda.com.br/)
* [LeadFormance](http://www.leadformance.com/)
* [23 Video](http://www.23video.com/)
* [CrystalCommerce](http://www.crystalcommerce.com/)
* [Rackspace](http://www.rackspace.com/)
* [Talent Technology](http://www.talenttech.com)
* [WebKite](http://webkite.com/)
* [Adam Ralph](http://adamralph.com/)
* [Quaderno](http://getquaderno.com/)
* [LocomotiveCMS](http://locomotivecms.com/)
* [Customer.io](http://customer.io)
* [Mixture.io](http://mixture.io)
* [MakePlans](http://makeplans.net)
* [Planning Center Services](http://get.planningcenteronline.com)
* [Planning Center Resources](http://get.planningcenteronline.com/resources)
* [RoQua](http://www.roqua.nl)
* [Evrone](http://www.evrone.com)
* [Liquid.as](https://github.com/prevailhs/liquid.as)
* [Open Liquid](https://github.com/23/openliquid)
* [500px](http://portfolios.500px.com)
* [VTEX](http://www.vtex.com.br/)
* [Xorcode](http://www.xorcode.com/)
* [MobiCheckin (registration forms)](http://www.mobicheckin.com)
* [Educative-Games.org](http://educative-games.org)
* [GiftFold](http://giftfold.com)
* [Reamaze](http://www.reamaze.com)
* [Sitebox.io](http://www.sitebox.io)
* [Stunning](https://bestunning.net)
* [Vero (Email Marketing Software)](https://www.getvero.com)
* [GoDaddy](https://www.godaddy.com)
* [SendOwl](http://www.sendowl.com)
* [FOX21.at](http://blog.fox21.at)
* [Bright Sites](http://www.brightsites.com)
* [Mode Analytics] (http://www.modeanalytics.com)
* [Helpjuice](https://www.helpjuice.com)
* [Freshdesk](http://freshdesk.com)
* [Continuity Control](http://www.continuity.net)
* [Mitingu](http://www.mitingu.com)
* [Festiment](http://www.festiment.com)
* [Unsound Music Festival](http://www.unsound.pl)
* [Expertory](http://www.expertory.com)
* [Appboy](https://www.appboy.com)
* [Disco](http://discolabs.com)
* [LavoWeb](http://lavoweb.net)
* [DediConcept](http://www.dediconcept.com)
* [Lucid](http://www.lucid.co.nz/)
* [Fedora](http://usefedora.com/)
* [Jumpseller](https://jumpseller.com/)
* [Openbay](https://www.openbay.com)
* [Sayan's Blog](http://sayan98.github.io/blog)
* [Industry Mailout](https://industrymailout.com/)
* [Near Me Marketplaces](https://near-me.com/)
* [Growing with the Web](http://www.growingwiththeweb.com/)
* [Mercury Flight](http://www.mercuryflight.com/)
* [Drip](https://www.getdrip.com/)
* [Sixty AS](http://www.sixty.no/)
* [Thinkific](http://www.thinkific.com/)
* [dotmailer](https://www.dotmailer.com/)
* ...Add yours :)

## Why should I use Liquid?

* You want to allow your users to edit the appearance of your application, but
  don't want them to run insecure code on your server.
* You want to render templates directly from the database.
* You like Smarty-style template engines.
* You need a template engine which does HTML just as well as emails.
* You don't like the markup language of your current template engine.