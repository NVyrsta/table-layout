<template>
  <section class="section">
    <h1 class="section__title">{{ msg }}</h1>

    <div class="dashboard">
      <div class="dashboard__panel">
        <button class="dashboard__btn secondary-btn" id="agree-orally-btn">
          Узгодити усно
        </button>

        <button class="dashboard__btn secondary-btn" id="delete-btn">
          Видалити
        </button>

        <button class="dashboard__btn primary-btn" id="add-spare-parts-btn">
          Додати запчастини
        </button>

        <button class="dashboard__btn primary-btn" id="add-kit-btn">
          Додати комплект
        </button>

        <button class="dashboard__btn primary-btn" id="go-warehouse-btn">
          Перейти на склад
        </button>
      </div>

      <div class="dashboard_table">
        <table class="table">
          <thead>
            <tr class="table__row">
              <th class="table__checkbox">
                <label class="checkbox-container">
                  <input type="checkbox" />
                  <span class="checkbox-custom"></span>
                </label>
              </th>

              <th class="table__article">Артикул</th>

              <th>Код товару</th>

              <th>Назва</th>

              <th>Ціна/од., ₴</th>

              <th>Кількість, шт/л</th>

              <th>Сума, ₴</th>

              <th></th>
            </tr>
          </thead>

          <tbody>
            <tr
              v-for="item in tableData"
              :key="item.id"
              :class="getStatusClass(item.status)"
              class="table__row"
            >
              <td class="table__checkbox cell">
                <label class="checkbox-container">
                  <input type="checkbox" />

                  <span class="checkbox-custom"></span>
                </label>
              </td>

              <td>{{ item.article }}</td>

              <td>{{ item.productCode }}</td>

              <td class="table__product-name">
                <a :href="item.url" target="_blank">{{ item.name }}</a>
              </td>

              <td>
                <a :href="item.url" target="_blank" class="text-highlight">{{
                  item.price
                }}</a>
              </td>

              <td>х{{ item.quantity }} шт.</td>

              <td>
                <a :href="item.url" target="_blank" class="text-highlight">{{
                  item.amount
                }}</a>
              </td>

              <td><button class="table__edit-btn"></button></td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'TableLayout',
  props: {
    msg: String,
  },
  data() {
    return {
      tableData: [
        {
          id: 1,
          article: '12312',
          productCode: 'L1MP1DD3V',
          name: 'Назва запчастини',
          url: 'https://fixiq.pro/',
          price: 200,
          quantity: 1,
          amount: 200,
          status: 'rejected',
        },
        {
          id: 2,
          article: '12312',
          productCode: 'L1MP1DU1UX',
          name: 'Назва запчастини',
          url: 'https://fixiq.pro/',
          price: 200,
          quantity: 1,
          amount: 200,
          status: 'agreed orally',
        },
        {
          id: 3,
          article: '12312',
          productCode: 'L1MP1DQA',
          name: 'Назва запчастини',
          url: 'https://fixiq.pro/',
          price: 200,
          quantity: 1,
          amount: 200,
          status: 'on agreement',
        },
        {
          id: 4,
          article: '12312',
          productCode: 'L1MP1DPR0D',
          name: 'Назва запчастини',
          url: 'https://fixiq.pro/',
          price: 200,
          quantity: 3,
          amount: 200,
          status: 'new',
        },
      ],
      selectAll: false,
    };
  },
  methods: {
    getStatusClass(status) {
      switch (status) {
        case 'new':
          return 'status-new';
        case 'rejected':
          return 'status-rejected';
        case 'on agreement':
          return 'status-on-agreement';
        case 'agreed orally':
          return 'status-agreed-orally';
        default:
          return '';
      }
    },
  },
};
</script>

<!-- Add "scoped" article to limit CSS to this component only -->
<style scoped>
.section {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  max-width: 1171px;
  width: 100%;
  padding: 24px 16px;
  gap: 16px;

  border-radius: 8px;
  background: var(--primary-white);
  box-shadow: 0px 6px 30px 0px rgba(62, 65, 71, 0.12);
}

.section__title {
  color: var(--primary-black);

  font-size: 20px;
  font-weight: 600;
  line-height: 28px;
}

.dashboard {
  width: 100%;

  border: 1px solid var(--gray-border);
  border-radius: 8px;
}

.dashboard__panel {
  display: flex;
  padding: 16px;
  align-items: center;

  border-bottom: 1px solid var(--gray-border);
}

.dashboard__btn {
  display: inline-flex;
}

.dashboard__btn::before {
  content: '';
  display: inline-block;
  margin-right: 8px;
  width: 16px;
  height: 16px;

  background-repeat: no-repeat;
  background-size: contain;
}

.dashboard__btn:nth-child(1)::before {
  background-image: url(../assets/icons/chat.svg);
}

.dashboard__btn:nth-child(2)::before {
  background-image: url(../assets/icons/trash.svg);
}

.dashboard__btn:nth-child(3)::before,
.dashboard__btn:nth-child(4)::before {
  background-image: url(../assets/icons/plus.svg);
}

.dashboard__btn:nth-child(5)::before {
  background-image: url(../assets/icons/box.svg);
}

.secondary-btn {
  color: var(--gray-600);

  text-align: center;
  font-size: 14px;
  font-family: Inter;
  line-height: 16px;

  cursor: not-allowed;
}

.dashboard__panel button:first-child {
  margin-right: 24px;
}

.primary-btn {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-right: 8px;
  padding: 10px 20px;

  border-radius: 12px;
  border: 1px solid var(--primary-accent-b-2-b);

  cursor: pointer;
}
.dashboard__panel button:last-child {
  margin-right: 0;
}

#add-spare-parts-btn {
  margin-left: auto;
}

.table {
  width: 100%;

  line-height: 20px;
}

.table tr {
  display: flex;
  padding: 16px;

  align-items: center;
  text-align: left;

  border-bottom: 1px solid var(--gray-border);
}

.table tbody tr:last-of-type {
  border-bottom: none;
}

.table__edit-btn {
  height: 16px;
  width: 16px;

  background-image: url(../assets/icons/pen.svg);
  background-repeat: no-repeat;
}

.table a {
  position: relative;

  transition: all 0.3s ease-in-out;
}

.checkbox-container {
  position: relative;
  display: inline-block;

  cursor: pointer;
}

.checkbox-container input {
  display: none;
}

.checkbox-custom {
  display: block;
  width: 16px;
  height: 16px;

  background-image: url(../assets/icons/checkbox.svg);
  background-repeat: no-repeat;
  background-position: center;
  background-size: contain;
}

.checkbox-container input:checked ~ .checkbox-custom {
  background-image: url(../assets/icons/check.png);
}

.text-highlight {
  position: relative;

  color: var(--primary-accent-b-2-c);

  text-align: right;
}

.text-highlight::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 100%;
  height: 2px;

  background-image: url(../assets/icons/border-bottom.svg);
  background-repeat: no-repeat;
  background-position: center bottom;
}

.table__checkbox {
  width: 16px;
  height: 16px;
  margin-right: 24px;
}

td {
  display: flex;
  justify-content: center;
  align-items: center;
}

.table__row {
  position: relative;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  padding: 16px;
}

.table__row::before {
  position: absolute;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  padding: 0px 16px;
  top: 0;
  left: 0;
  height: 16px;

  border-radius: 0px 0px 12px 0px;

  font-size: 10px;
  line-height: 16px;
}

.table__row td {
  padding: 10px 0;
}

.status-new::before {
  content: 'Нова';
  background: rgba(76, 107, 255, 0.1);
  color: var(--primary-accent-b-2-c);
}

.status-rejected::before {
  content: 'Відхилено';
  background: var(--all-red-50);
  color: var(--secondary-red);
}

.status-agreed-orally::before {
  content: 'Узгоджено усно';
  color: var(--secondary-purple);
  background: #f2e6fa;
}

.status-on-agreement::before {
  content: 'На узгодженні';
  background: rgba(250, 141, 26, 0.1);
  color: var(--secondary-orange);
}

tr th,
tr td {
  display: inline-flex;
  justify-content: flex-start;
  align-items: center;
  width: 100%;
}

td:last-child {
  justify-content: flex-end;
}

.table__product-name::after {
  content: '';
  width: 16px;
  margin-left: 8px;
  height: 16px;

  background-image: url(../assets/icons/link.svg);
  background-repeat: no-repeat;
  background-size: contain;
}

.table__product-name a:hover {
  position: relative;
  color: var(--primary-accent-b-2-c);

  text-align: right;
}

.table__product-name a:hover::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 100%;
  height: 2px;

  background-image: url(../assets/icons/border-bottom.svg);
  background-repeat: no-repeat;
  background-position: center bottom;
}

td,
th {
  margin-right: 24px;
}

th:nth-child(4),
td:nth-child(4) {
  max-width: 50%;
}

th:nth-child(5),
td:nth-child(5),
th:nth-child(6),
td:nth-child(6),
th:nth-child(7),
td:nth-child(7) {
  justify-content: flex-end;
}
</style>
