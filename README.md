# image-swhcher-with-tab-and-accordian


<script>
    
document.addEventListener('DOMContentLoaded', () => {

    function setupImageSwitchers(selector) {
        
        let imageSwitchers = Array.from(document.querySelectorAll(`${selector} .videoSwitcherWrapper`));
        imageSwitchers.forEach(imageSwitcher => {
            let images = imageSwitcher.querySelectorAll('.videoSwitcherTab');
            let tabsTitlesDesktop = imageSwitcher.querySelectorAll('.e-n-tabs-heading .e-n-tab-title');
            let tabsTitles = imageSwitcher.querySelectorAll('.elementor-tab-title');
            let accordionTitles = imageSwitcher.querySelectorAll('.e-n-accordion-item-title');

            tabsTitlesDesktop.forEach((tab, index) => {
                tabsChanging(tab, index, images);
            });

            tabsTitles.forEach((tab, index) => {
                tabsChanging(tab, index, images);
            });

            accordionTitles.forEach((tab, index) => {
                tabsChanging(tab, index, images);
            });

            /* on page load */
            images[0].classList.add('videoSwitcher_isActive');

        });
    }
    
    setupImageSwitchers('');

    /* compatibility for Elementor popups */
    jQuery(document).on('elementor/popup/show', () => {
        setupImageSwitchers('.elementor-popup-modal');
    });

    function tabsChanging(tab, index, images) {
        tab.addEventListener('click', () => {
            images.forEach(image => {
                image.classList.remove('videoSwitcher_isActive');
            });
            images[index].classList.add('videoSwitcher_isActive');
        });
    };

});

</script>
<style>
body:not(.elementor-editor-active) .videoSwitcherTab:not(:first-child) {
    position: absolute;
    transition: opacity 0.4s;
}
body:not(.elementor-editor-active) .videoSwitcherTab {
    opacity: 0;
}
.videoSwitcherTab.videoSwitcher_isActive.videoSwitcher_isActive {
    opacity: 1;
}
</style>
