# Cybersecurity_Project
//Telegram bot
// Create your bot passing the token received from @BotFather
TelegramBot bot = new TelegramBot("BOT_TOKEN");

// Register for updates
bot.setUpdatesListener(updates -> {
    // ... process updates
    // return id of last processed update or confirm them all
    return UpdatesListener.CONFIRMED_UPDATES_ALL;
});

// Send messages
long chatId = update.message().chat().id();
SendResponse response = bot.execute(new SendMessage(chatId, "Hello!"));

TelegramBot bot = new TelegramBot("BOT_TOKEN");
BaseResponse response = bot.execute(request);
bot.execute(request, new Callback() {
    @Override
    public void onResponse(BaseRequest request, BaseResponse response) {
    
    }
    @Override
    public void onFailure(BaseRequest request, IOException e) {
    
    }
});

class Update {
    Integer updateId();
    Message message();
    Message editedMessage();
    InlineQuery inlineQuery();
    ChosenInlineResult chosenInlineResult();
    CallbackQuery callbackQuery();
}
GetUpdates getUpdates = new GetUpdates().limit(100).offset(0).timeout(0);

// sync
GetUpdatesResponse updatesResponse = bot.execute(getUpdates);
List<Update> updates = updatesResponse.updates();
...
Message message = update.message()


// async
bot.execute(getUpdates, new Callback<GetUpdates, GetUpdatesResponse>() {
    @Override
    public void onResponse(GetUpdates request, GetUpdatesResponse response) {
        List<Update> updates = response.updates();
    }
    
    @Override
    public void onFailure(GetUpdates request, IOException e) {
    
    }
});
  
  ChatAction action = ChatAction.typing;
  ChatAction action = ChatAction.upload_photo;
  ChatAction action = ChatAction.find_location;
  SendMessage request = new SendMessage(chatId, "text")
        .parseMode(ParseMode.HTML)
        .disableWebPagePreview(true)
        .disableNotification(true)
        .replyToMessageId(1)
        .replyMarkup(new ForceReply());

  // sync
  SendResponse sendResponse = bot.execute(request);
  boolean ok = sendResponse.isOk();
  Message message = sendResponse.message();

  // async
  bot.execute(request, new Callback<SendMessage, SendResponse>() {
      @Override
      public void onResponse(SendMessage request, SendResponse response) {

      }

      @Override
      public void onFailure(SendMessage request, IOException e) {

      }
  });
  
