<h1 dir="auto"><a id="user-content-задание-1-синдром-100-обязательное-к-выполнению" class="anchor" aria-hidden="true" href="#задание-1-синдром-100-обязательное-к-выполнению"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Задание 1. Синдром 100% (обязательное к выполнению)</h1>
<p dir="auto">Вы попали в команду максималистов, которые хотят, чтобы те авто-тесты, которые вы пишете, покрывали код на 100%.</p>
<p dir="auto">Но вот незадача:</p>
<ol dir="auto">
<li>Непонятно, что такое 100%</li>
<li>Непонятно, как это сделать</li>
</ol>
<p dir="auto">Вспоминаем: покрытием кода у нас занимается JaCoCo, но он просто "сигнализирует" о том, что конкретно пошло не так.</p>
<p dir="auto">Большинство подобных плагинов помимо целей отчётности (<code>report</code>) содержат ещё цель <code>check</code>, которая обрушает сборку, если не выполнены определённые проверки.</p>
<p dir="auto">Что вам нужно:</p>
<ol dir="auto">
<li>Создать мавен-проект с тестируемым кодом из листинга кода (указан ниже по условию)</li>
<li>Изучить <a href="https://www.eclemma.org/jacoco/trunk/doc/maven.html" rel="nofollow">документацию на плагин</a> (а конкретно на цель <code>check</code>)</li>
<li>Внедрить эту цель в фазу <code>verify</code> (обратите внимание, что эта цель итак публикуется в эту фазу)</li>
<li>Настроить правила по покрытию на 100% (при этом нужно изучить разницу между счётчиками <code>INSTRUCTION</code>, <code>LINE</code>, <code>BRANCH</code>, <code>COMPLEXITY</code>)</li>
<li>Вникнуть в тестируемый код</li>
<li>Выбрать один из счётчиков и добиться 100% покрытия через добавление новых тестов</li>
</ol>
<p dir="auto"><strong>Важно</strong>: использовать можно только один из следующих:</p>
<ol dir="auto">
<li><code>INSTRUCTION</code></li>
<li><code>LINE</code></li>
<li><code>BRANCH</code></li>
</ol>
<p dir="auto">Обратите внимание на чеклист в начале условия, он содержит подсказки по внедрению JaCoCo в ваш мавен-проект.</p>
<p dir="auto">Тестируемый код (его как-либо редактировать <strong>нельзя</strong>):</p>
<div class="highlight highlight-source-java notranslate position-relative overflow-auto"><pre><span class="pl-k">package</span> <span class="pl-s1">ru</span>.<span class="pl-s1">netology</span>.<span class="pl-s1">statistic</span>;

public class StatisticsService {
 
  public long findMax(long[] incomes) {
    long current_max_index = 0;
    long current_max = incomes[0];
    for (long income : incomes)
      if (current_max < income)
        current_max = income;
        return current_max;
  }
}
</div>
<p dir="auto">Класс с тестами (его надо будет расширить новыми тестами):</p>
<div class="highlight highlight-source-java notranslate position-relative overflow-auto"><pre><span class="pl-k">package</span> <span class="pl-s1">ru</span>.<span class="pl-s1">netology</span>.<span class="pl-s1">statistic</span>;
import org.junit.jupiter.api.Test;

import static org.junit.jupiter.api.Assertions.*;

public class StatisticsServiceTest {

  @Test
  void findMax() {
    StatisticsService service = new StatisticsService();

    long[] incomesInBillions = {12, 5, 8, 4, 5, 3, 8, 6, 11, 11, 12};
    long expected = 12;

    long actual = service.findMax(incomesInBillions);

    assertEquals(expected, actual);
  }
}
</div>
<p dir="auto">Итого: отправьте на проверку ссылку на гитхаб-репозиторий с вашим проектом.</p>
