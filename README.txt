THIS SOFTWARE IS NO LONGER BEING MAINTAINED. VERSION 1.1.4 IS THE FINAL RELEASE.
IF YOU WOULD LIKE TO MAKE YOUR OWN UPDATES, YOU CAN FORK IT. PULL REQUESTS TO
THIS REPOSITORY WILL BE IGNORED.

Download latest version of ReportNG from either of the following:

https://dl.dropboxusercontent.com/u/14133069/reportng-1.1.4.tgz
https://dl.dropboxusercontent.com/u/14133069/reportng-1.1.4.zip

Full instructions on how to use ReportNG can be found here:

http://reportng.uncommons.org

修改记录
修改中文乱码问题
在1.1.4的基础上新增截图展示的功能
引人新的reportng包并在测试用例中调用方法
public void screenShot() {
        //生成时间戳
        String dateString = DateUtil.formatDate(new Date(),"yyyy-MM-dd-HHmmss");
        String dir_name=ConfigUtil.getSystemConfig("screen.path");

        //调用方法捕捉画面
        File screen=androidDriver.getScreenshotAs(OutputType.FILE);
        log.info("本次用例截取图片目录：",dir_name);

        //复制文件到指定目录
        //图片最后存放的路径由 目录：dir_name +时间戳+测试套件+测试用例+测试步骤组合生成
        System.out.println("用例图片名称"+dir_name+"\\"+dateString+".jpg");

        try {
            FileUtils.copyFile(screen,new File(dir_name+"\\"+dateString+".jpg"));
            Reporter.log("<img src='"+dateString+".jpg' hight='100' width='100'/>");
        } catch (IOException e) {
            log.info("跑用例时截取图片失败。。。");
            e.printStackTrace();
        }

    }