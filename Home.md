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
* [Edicy](http://www.edicy.com)
* [Workory](http://www.workory.com)
* [Zendesk](http://www.zendesk.com)
* [SandwichBoard](http://www.sandwichboard.com/)
* [YikeSite (CMS)](http://api.yikesite.com/)
* [Simplicant (Applicant Tracking System)](http://www.simplicant.com/)
* [3scale (API Management System)](http://www.3scale.net/)
* [Chaptercore](http://www.chaptercore.com)
* [ScreenSteps Live](http://bluemangolearning.com/screenstepslive)
* [PokerAffiliateSolutions](http://www.pokeraffiliatesolutions.com/)
* [Desk.com](http://www.desk.com)
* [Ronin](http://www.roninapp.com)
* [CrowdVine](http://www.crowdvine.com)
* [AboutOne](http://www.aboutone.com)
* [RightScale](http://support.rightscale.com/15-References/Liquid_Markup_with_RightScale_Widgets)
* [Menumill](http://www.menumill.com)
* [Moxie Software](http://www.moxiesoft.com/)
* [Rusic](http://rusic.com/)
* [Development Seed](http://developmentseed.org/blog/2011/09/09/jekyll-github-pages/)
* [peerTransfer](http://peertransfer.com)
* [NationBuilder](http://nationbuilder.com/)
* [Vendder](http://vendder.com/)
* [tradelr](http://www.tradelr.com)
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
* [Xeemio](http://www.xeemio.com/)
* [LeadFormance](http://www.leadformance.com/)
* [23 Video](http://www.23video.com/)
* [CrystalCommerce](http://www.crystalcommerce.com/)
* [Rackspace](http://www.rackspace.com/)
* [Savory](http://www.savory.io/)
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
* ...Add yours :)

## Why should I use Liquid?

* You want to allow your users to edit the appearance of your application, but
  don't want them to run insecure code on your server.
* You want to render templates directly from the database.
* You like Smarty-style template engines.
* You need a template engine which does HTML just as well as emails.
* You don't like the markup language of your current template engine.