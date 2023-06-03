const { chromium } = require('playwright');

async function runTest() {
  const browser = await chromium.launch();
  const context = await browser.newContext();
  const page = await context.newPage();
  
  // Шаг 1: Перейти на главную "www.sima-land.ru"
  await page.goto('https://www.sima-land.ru');
  
  // Шаг 2: В хедере нажать на кнопку "Войти"
  await page.click('text=Войти');
  
  // Шаг 3: Ввести логин: qa_test@test.ru
  await page.fill('input[name="USER_LOGIN"]', 'qa_test@test.ru');
  
  // Шаг 4: Ввести пароль: qa_test
  await page.fill('input[name="USER_PASSWORD"]', 'qa_test');
  
  // Шаг 5: Нажать кнопку "Войти"
  await Promise.all([
    page.waitForNavigation(), // Ожидание перехода после нажатия кнопки
    page.click('button[name="Login"]')
  ]);
  
  // Шаг 6: Проверить, что авторизация прошла успешно
  const pageTitle = await page.title();
  if (pageTitle === 'Личный кабинет') {
    console.log('Авторизация прошла успешно');
  } else {
    console.log('Авторизация не удалась');
  }
  
  await browser.close();
}

runTest();