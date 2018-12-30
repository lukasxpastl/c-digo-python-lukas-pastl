# c-digo-python-lukas-pastl
import discord
import asyncio
import secreto

client = discord.Client()

COR = 0x2B1465
TOKEN = secreto.seu_token()
msg_id = None
msg_user = None


@client.event
async def on_realy():
    print('Bot Online - olá mundo!')
    print(client.user.name)
    print(client.user.id)
    print('-------NeagleHouse3.0---------')


@client.event
async def on_message(message):
    if message.content.lower().startswith('?idade'):
        embed1 = discord.embed(
            titler="Você é maior ou menor de idade?",
            Color=COR,
            description="18+ = 💋\n"
                        "18- = 🔞",)

    botmsg = await client.send_message(message.channel, embed = embed1)
    await client.add_reaction(botmsg, "💋")
    await client.add_reaction(botmsg, "🔞")

    @client.event
    async def on_message(message):
        global embed
        if message.content.lower().startswith('?estado'):
            embed1 = discord.embed(
                titler="Qual o estado que você mora?",
                Color=COR,
                description="Norte = 🌐\n"
                            "Nordeste = 🌞\n"
                            "Sul = 🌝\n"
                            "Sudeste = 🌚",)

        botmsg = await client.send_message(message.channel, embed = embed1)
        await client.add_reaction(botmsg, "🌐")
        await client.add_reaction(botmsg, "🌞")
        await client.add_reaction(botmsg, "🌝")
        await client.add_reaction(botmsg, "🌚")

    global msg_id
    msg_id = botmsg.id
    global msg_user
    msg_user = botmsg.author

@client.event
async def on_reaction_add(reaction, user):
    msg = reaction.message


    if reaction.emoji == "💋" and msg.id == msg_id: #and user == msg_user:
        role = discord.utils.find(lambda r: r.name == "18+", msg.server.roles)
        await client.add_roles(user, role)
        print("Cargo Adicionado")

    if reaction.emoji == "🔞" and msg.id == msg_id: #and user == msg_user:
        role = discord.utils.find(lambda r: r.name == "18-", msg.server.roles)
        await client.add_roles(User, role)
        print("Cargo Adicionado")

    if reaction.emoji == "🌐" and msg.id == msg_id: #and user == msg_user:
        role = discord.utils.find(lambda r: r.name == "Norte", msg.server.roles)
        await client.add_roles(User, role)
        print("Cargo Adicionado")

    if reaction.emoji == "🌞" and msg.id == msg_id: #and user == msg_user:
        role = discord.utils.find(lambda r: r.name == "Nordeste", msg.server.roles)
        await client.add_roles(User, role)
        print("Cargo Adicionado")

    if reaction.emoji == "🌝" and msg.id == msg_id: #and user == msg_user:
        role = discord.utils.find(lambda r: r.name == "Sul", msg.server.roles)
        await client.add_roles(User, role)
        print("Cargo Adicionado")

    if reaction.emoji == "🌚" and msg.id == msg_id: #and user == msg_user:
        role = discord.utils.find(lambda r: r.name == "Sudeste", msg.server.roles)
        await client.add_roles(User, role)
        print("Cargo Adicionado")

@client.event
async def on_reaction_remove(reaction, user):
    msg = reaction.message

    if reaction.emoji == "💋" and msg.id == msg_id: #and user == msg_user:
        role = discord.utils.find(lambda r: r.name == "18+", msg.server.roles)
        await client.add_roles(user, role)
        print("Cargo removido")


    if reaction.emoji == "🔞"  and msg.id == msg_id: #and user == msg_user:
        role = discord.utils.find(lambda r: r.name == "18-", msg.server.roles)
        await client.add_roles(user, role)
        print("Cargo removido")

    if reaction.emoji == "🌐"  and msg.id == msg_id: #and user == msg_user:
        role = discord.utils.find(lambda r: r.name == "Norte", msg.server.roles)
        await client.add_roles(user, role)
        print("Cargo removido")

    if reaction.emoji == "🌞"  and msg.id == msg_id: #and user == msg_user:
        role = discord.utils.find(lambda r: r.name == "Nordeste", msg.server.roles)
        await client.add_roles(user, role)
        print("Cargo removido")

    if reaction.emoji == "🌝"  and msg.id == msg_id: #and user == msg_user:
        role = discord.utils.find(lambda r: r.name == "Sul", msg.server.roles)
        await client.add_roles(user, role)
        print("Cargo removido")

    if reaction.emoji == "🌚"  and msg.id == msg_id: #and user == msg_user:
        role = discord.utils.find(lambda r: r.name == "Sudeste", msg.server.roles)
        await client.add_roles(user, role)
        print("Cargo removido")

client.run(TOKEN)
