// state
export const state = () => ({
  formData: [],
  formSubmitted: false, // Додали стан для відстеження відправлення форми
  formError: null, // Додали стан для відстеження помилок
});

// getters
export const getters = {
  getFormData: (state) => state.formData,
};

// actions
export const actions = {
  async getForms({ commit }, formData) {
    try {
      const response = await axios.post("https://randomform.me./api/?results=10", formData);
      commit("addForm", response.data);
      commit("setFormSubmitted", true); // Встановлюємо прапорець відправленої форми
      commit("setFormError", null); // Очищаємо помилки, якщо вони були
      return response.data;
    } catch (error) {
      commit("setFormError", "Помилка під час відправлення форми"); // Зберігаємо помилку
      console.error("Error while fetching data:", error);
    }
  },
};

// mutations
export const mutations = {
  addForm(state, formData) {
    state.formData.push(...formData);
  },
  setFormSubmitted(state, submitted) {
    state.formSubmitted = submitted;
  },
  setFormError(state, error) {
    state.formError = error;
  },
};
