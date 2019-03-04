# TestGit
Checking Git
var LoginPage = require('../pages/login.js');
var Testdata = require('../constantdata/Testdata.json');
var logger = require('../Resources/Winstonlogger.js')
var EC = protractor.ExpectedConditions;
var text;
var addStorePage = function(){

    this.verifyaddStorePopup = function(){
        browser.wait(EC.visibilityOf(element(by.id("plato-coworker-dialog"))),500)
    };
    this.verifyStartDateField = function(){
        browser.sleep(200)
        browser.wait(EC.visibilityOf(element(by.id("addcoworker-start-date-picker-input"))),500)
        expect(element(by.id("addcoworker-start-date-picker-input")).isPresent()).toEqual(true);
    };
    this.inputCoworkerSearch = function(text){
        browser.wait(EC.visibilityOf(element(by.id("search-coworker-input"))), 1500)
        element(by.id("search-coworker-input")).sendKeys(text)
    };
    this.selectsearchiteam = function(){
        browser.wait(EC.visibilityOf(element(by.xpath("//*[contains(text(),'Veerle Fastenaekels (F822) - Halle (3515)')]"))), 1500);
        browser.sleep(1000)
        var elm = element(by.xpath("//*[contains(text(),'Veerle Fastenaekels (F822) - Halle (3515)')]"))
        browser.executeScript("$(arguments[0]).click();", elm)
    };
    this.clickOnincomingTransferSearchiteam = function () {
        browser.wait(EC.visibilityOf(element(by.xpath("//*[contains(text(),'Thanuja Mudiyala')]"))), 1000)
        element(by.xpath("//*[contains(text(),'Thanuja Mudiyala')]")).click();
    };
    this.enterStartDate = function (text) {
        browser.wait(EC.visibilityOf(element(by.id("addcoworker-start-date-picker-input"))), 1000)
        browser.driver.findElement(by.id("addcoworker-start-date-picker-input")).sendKeys(text)
    };
    this.entererrmsgStartDate = function (text) {
        browser.wait(EC.visibilityOf(element(by.id("addcoworker-start-date-picker-input"))), 500)
        browser.driver.findElement(by.id("addcoworker-start-date-picker-input")).click()
        browser.driver.findElement(by.id("addcoworker-start-date-picker-input")).sendKeys(text)
    };
    this.verifyPastDateBorderColor= function(borderColor) {
        return element(by.id("addcoworker-start-date-picker-input")).getCssValue("border-color").then(function (text) {
            expect(text).toBe(borderColor)
        })
    };
    this.clickOnStartDateField = function(text){
        browser.wait(EC.visibilityOf(element(by.className("ui-button-icon-left ui-clickable pi pi-calendar"))), 1000)
        browser.driver.findElement(by.className("ui-button-icon-left ui-clickable pi pi-calendar")).click()
        browser.sleep(500)
    };
    this.verifyDatepicker= function() {
        expect(element(by.className("ui-datepicker-calendar")).isDisplayed()).toBe(true)
        logger.log("info","datePicker is displayed")
    };
    this.verifyAliasName= function(strVal) {
        browser.sleep(1000)
        element(by.className("form-control ng-untouched ng-pristine ng-valid")).getAttribute('value').then(function (text) {
            expect(text).toEqual(strVal)
        })
    };
    this.enterEndDate = function (text) {
        browser.wait(EC.visibilityOf(element(by.id("addcoworker-end-date-picker-input"))), 500)
        browser.driver.findElement(by.id("addcoworker-end-date-picker-input")).sendKeys(text)
    };
    this.SaveButtoninAddStorePage = function () {
        browser.wait(EC.visibilityOf(element(by.id("addcoworker-dialog-save-button"))), 500);
        return element(by.id("addcoworker-dialog-save-button")).click();
    };
    this.CancelButtoninAddStorePage = function () {
        browser.wait(EC.visibilityOf(element(by.id("addcoworker-dialog-cancel-button"))), 500);
        return element(by.id("addcoworker-dialog-cancel-button")).click();
    };
}
module.exports = new addStorePage();
